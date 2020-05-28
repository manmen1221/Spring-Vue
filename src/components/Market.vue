<template>
  <el-container>
    <el-main>
      <el-header>
        <div style="float: left">
          账号：{{us}}
          <el-button @click="修改密码按钮()" type="info" plain>修改密码</el-button>
        </div>
        <div style="float: right">
          <el-button @click="退出登录()" type="primary" plain>退出登录</el-button>
        </div>
      </el-header>
      <el-tabs type="border-card">
        <el-tab-pane label="交易系统">
          <el-container direction='vertical'>
            <div>
              <div style="float: left">
                <el-button @click="刷新交易系统表()" type="primary" plain>刷新</el-button>
              </div>
              <div style="float: right">
                <el-button @click="新交易()" type="success" plain>新交易</el-button>
              </div>
            </div>
            <el-divider/>
            <el-tabs type="border-card" tab-position="left" >
              <el-tab-pane label="已公开交易">
                <div class="block">
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J1($event)" :current-page="表格数据.交易系统.当前显示页数.p1" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z1"/>
                  <el-table height="1000px" :data="表格数据.交易系统.内容.t1">
                    <el-table-column prop="交易标题" label="交易"/>
                    <el-table-column prop="用户" label="卖家" width="200" fixed="right"/>
                    <el-table-column prop="创建时间" label="时间" width="200" fixed="right"/>
                    <el-table-column prop="交易状态" label="状态" width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-tag :type="取标签(scope.row.交易状态)" disable-transitions>{{scope.row.交易状态}}</el-tag>
                      </template>
                    </el-table-column>
                    <el-table-column width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-button type="primary" plain @click="查看详情J1(scope.row)">详情</el-button>
                      </template>
                    </el-table-column>
                  </el-table>
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J1($event)" :current-page="表格数据.交易系统.当前显示页数.p1" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z1"/>
                </div>
              </el-tab-pane>
              <el-tab-pane label="出售的交易">
                <div class="block">
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J2($event)" :current-page="表格数据.交易系统.当前显示页数.p2" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z2"/>
                  <el-table height="1000px" :data="表格数据.交易系统.内容.t2">
                    <el-table-column prop="交易标题" label="交易"/>
                    <el-table-column prop="用户" label="卖家" width="200" fixed="right"/>
                    <el-table-column prop="创建时间" label="时间" width="200" fixed="right"/>
                    <el-table-column prop="交易状态" label="状态" width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-tag :type="取标签(scope.row.交易状态)" disable-transitions>{{scope.row.交易状态}}</el-tag>
                      </template>
                    </el-table-column>
                    <el-table-column width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-button type="primary" plain @click="查看详情J2(scope.row)">详情</el-button>
                      </template>
                    </el-table-column>
                  </el-table>
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J2($event)" :current-page="表格数据.交易系统.当前显示页数.p2" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z2"/>
                </div>
              </el-tab-pane>
              <el-tab-pane label="已失效出售">
                <div class="block">
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J3($event)" :current-page="表格数据.交易系统.当前显示页数.p3" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z3"/>
                  <el-table height="1000px" :data="表格数据.交易系统.内容.t3">
                    <el-table-column prop="交易标题" label="交易"/>
                    <el-table-column prop="用户" label="卖家" width="200" fixed="right"/>
                    <el-table-column prop="创建时间" label="时间" width="200" fixed="right"/>
                    <el-table-column prop="交易状态" label="状态" width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-tag :type="取标签(scope.row.交易状态)" disable-transitions>{{scope.row.交易状态}}</el-tag>
                      </template>
                    </el-table-column>
                    <el-table-column width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-button type="primary" plain @click="查看详情J3(scope.row)">详情</el-button>
                      </template>
                    </el-table-column>
                  </el-table>
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J3($event)" :current-page="表格数据.交易系统.当前显示页数.p3" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z3"/>
                </div>
              </el-tab-pane>
              <el-tab-pane label="购买的交易">
                <div class="block">
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J4($event)" :current-page="表格数据.交易系统.当前显示页数.p4" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z4"/>
                  <el-table height="1000px" :data="表格数据.交易系统.内容.t4">
                    <el-table-column prop="交易标题" label="交易"/>
                    <el-table-column prop="卖家" label="卖家" width="200" fixed="right"/>
                    <el-table-column prop="创建时间" label="时间" width="200" fixed="right"/>
                    <el-table-column prop="买家" label="买家" width="200" fixed="right"/>
                    <el-table-column prop="申请时间" label="申请时间" width="200" fixed="right"/>
                    <el-table-column prop="申请状态" label="状态" width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-tag :type="取标签(scope.row.申请状态)" disable-transitions>{{scope.row.申请状态}}</el-tag>
                      </template>
                    </el-table-column>
                    <el-table-column width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-button type="primary" plain @click="查看详情J4(scope.row)">详情</el-button>
                      </template>
                    </el-table-column>
                  </el-table>
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J4($event)" :current-page="表格数据.交易系统.当前显示页数.p4" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z4"/>
                </div>
              </el-tab-pane>
              <el-tab-pane label="已失效购买">
                <div class="block">
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J5($event)" :current-page="表格数据.交易系统.当前显示页数.p5" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z5"/>
                  <el-table height="1000px" :data="表格数据.交易系统.内容.t5">
                    <el-table-column prop="交易标题" label="交易"/>
                    <el-table-column prop="卖家" label="卖家" width="200" fixed="right"/>
                    <el-table-column prop="创建时间" label="时间" width="200" fixed="right"/>
                    <el-table-column prop="买家" label="买家" width="200" fixed="right"/>
                    <el-table-column prop="申请时间" label="申请时间" width="200" fixed="right"/>
                    <el-table-column prop="申请状态" label="状态" width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-tag :type="取标签(scope.row.申请状态)" disable-transitions>{{scope.row.申请状态}}</el-tag>
                      </template>
                    </el-table-column>
                    <el-table-column width="100" fixed="right">
                      <template slot-scope="scope">
                        <el-button type="primary" plain @click="查看详情J5(scope.row)">详情</el-button>
                      </template>
                    </el-table-column>
                  </el-table>
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J5($event)" :current-page="表格数据.交易系统.当前显示页数.p5" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z5"/>
                </div>
              </el-tab-pane>
              <el-tab-pane label="已完成交易">
              <div class="block">
                  <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J6($event)" :current-page="表格数据.交易系统.当前显示页数.p6" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z6"/>
                  <el-table height="1000px" :data="表格数据.交易系统.内容.t6">
                      <el-table-column prop="交易标题" label="交易"/>
                      <el-table-column prop="卖家" label="卖家" width="200" fixed="right"/>
                      <el-table-column prop="创建时间" label="时间" width="200" fixed="right"/>
                      <el-table-column prop="买家" label="买家" width="200" fixed="right"/>
                      <el-table-column prop="申请时间" label="购买时间" width="200" fixed="right"/>
                      <el-table-column prop="申请状态" label="状态" width="100" fixed="right">
                        <template slot-scope="scope">
                          <el-tag :type="取标签(scope.row.申请状态)" disable-transitions>{{scope.row.申请状态}}</el-tag>
                        </template>
                      </el-table-column>
                      <el-table-column width="100" fixed="right">
                        <template slot-scope="scope">
                          <el-button type="primary" plain @click="查看详情J6(scope.row)">详情</el-button>
                        </template>
                      </el-table-column>
                    </el-table>
                    <el-pagination @size-change="更改单页显示条数($event)" @current-change="跳转到页J6($event)" :current-page="表格数据.交易系统.当前显示页数.p6" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.交易系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.交易系统.总条数.z6"/>
                  </div>
                </el-tab-pane>
            </el-tabs>
          </el-container>
        </el-tab-pane>
        <el-tab-pane label="审核系统" :disabled="关闭审核">
          <el-container direction='vertical'>
            <div>
              <div style="float: left">
                <el-button @click="刷新交易系统表()" type="primary" plain>刷新</el-button>
              </div>
            </div>
            <el-divider/>
            <el-pagination @size-change="更改单页显示条数S($event)" @current-change="跳转到页S($event)" :current-page="表格数据.审核系统.当前显示页数" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.审核系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.审核系统.总条数"/>
            <el-container>
            <el-table height="1000px" :data="表格数据.审核系统.内容">
              <el-table-column prop="交易标题" label="交易"/>
              <el-table-column prop="用户" label="卖家" width="200" fixed="right"/>
              <el-table-column prop="创建时间" label="时间" width="200" fixed="right"/>
              <el-table-column prop="交易状态" label="状态" width="100" fixed="right">
                <template slot-scope="scope">
                  <el-tag :type="取标签(scope.row.交易状态)" disable-transitions>{{scope.row.交易状态}}</el-tag>
                </template>
              </el-table-column>
              <el-table-column width="100" fixed="right">
                <template slot-scope="scope">
                  <el-button type="primary" plain @click="查看详情S(scope.row)">详情</el-button>
                </template>
              </el-table-column>
            </el-table>
            </el-container>
            <el-pagination @size-change="更改单页显示条数S($event)" @current-change="跳转到页S($event)" :current-page="表格数据.审核系统.当前显示页数" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.审核系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.审核系统.总条数"/>
          </el-container>
        </el-tab-pane>
        <el-tab-pane label="账号管理系统" :disabled="关闭管理">
          <el-container direction='vertical'>
            <div>
              <div style="float: left">
                <el-button @click="刷新管理系统表()" type="primary" plain>刷新</el-button>
              </div>
            </div>
            <div><div style="float: left">
              权限筛选：
              <el-radio-group v-model="表格数据.管理系统.权限筛选" @change="刷新管理系统表()">
                <el-radio-button label="全部"/>
                <el-radio-button label="普通"/>
                <el-radio-button label="审核"/>
                <el-radio-button label="管理员"/>
              </el-radio-group>
            </div></div>
            <div><div style="float: left">
              状态筛选：
              <el-radio-group v-model="表格数据.管理系统.状态筛选" @change="刷新管理系统表()">
                <el-radio-button label="全部"/>
                <el-radio-button label="正常"/>
                <el-radio-button label="审核"/>
                <el-radio-button label="封禁"/>
              </el-radio-group>
            </div></div>
            <el-divider/>
            <el-pagination @size-change="更改单页显示条数G($event)" @current-change="跳转到页G($event)" :current-page="表格数据.管理系统.当前显示页数" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.管理系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.管理系统.总条数"/>
            <el-container>
              <el-table height="1000px" :data="表格数据.管理系统.内容">
                <el-table-column prop="用户" label="用户"/>
                <el-table-column prop="创建时间" label="创建时间"/>
                <el-table-column prop="权限" label="权限">
                  <template slot-scope="scope">
                    <el-select v-model="scope.row.权限" @change="保存用户(scope.row)">
                      <el-option v-for="item in 表格数据.管理系统.权限选择" :key="item" :label="item" :value="item"/>
                    </el-select>
                  </template>
                </el-table-column>
                <el-table-column prop="状态" label="状态">
                  <template slot-scope="scope">
                    <el-select v-model="scope.row.状态" @change="保存用户(scope.row)">
                      <el-option v-for="item in 表格数据.管理系统.状态选择" :key="item" :label="item" :value="item"/>
                    </el-select>
                  </template>
                </el-table-column>
                <el-table-column label="重置密码">
                  <template slot-scope="scope">
                    <el-button type="danger" @click="重置密码(scope.row)">重置密码</el-button>
                  </template>
                </el-table-column>
              </el-table>
            </el-container>
            <el-pagination @size-change="更改单页显示条数G($event)" @current-change="跳转到页G($event)" :current-page="表格数据.管理系统.当前显示页数" :page-sizes="表格数据.交易系统.单页显示选择" :page-size="表格数据.管理系统.单页显示数量" layout="prev, pager, next, jumper, sizes, total" :total="表格数据.管理系统.总条数"/>
          </el-container>
        </el-tab-pane>
      </el-tabs>
      <el-dialog :visible.sync="表格数据.交易系统.详情弹窗.显示" destroy-on-close :close-on-click-modal="false">
        <div style="height:500px;">
            <el-scrollbar style="height:100%">
              <el-form :model="表格数据.交易系统.详情弹窗" ref="详情弹窗" status-icon width="100%">
                <el-form-item prop="交易标题">
                  <el-input placeholder="请输入内容" maxlength="50" show-word-limit v-model="表格数据.交易系统.详情弹窗.交易标题" :disabled="表格数据.交易系统.详情弹窗.禁用修改" width="100%"/>
                </el-form-item>
                <div style="float: left">卖家：{{表格数据.交易系统.详情弹窗.卖家}} ----- 时间：{{表格数据.交易系统.详情弹窗.创建时间}}</div>
                <el-form-item prop="交易内容">
                  <el-input placeholder="请输入内容" :autosize="{ minRows: 10, maxRows: 10}" maxlength="1000" type="textarea" resize="none" v-model="表格数据.交易系统.详情弹窗.交易内容" :disabled="表格数据.交易系统.详情弹窗.禁用修改" width="100%"/>
                </el-form-item>
                <el-button plain type="primary" @click="详情弹窗功能按钮()" :disabled="表格数据.交易系统.详情弹窗.按钮1禁用">{{表格数据.交易系统.详情弹窗.按钮1}}</el-button>
                <el-button plain @click="关闭详情弹窗()">{{表格数据.交易系统.详情弹窗.按钮2}}</el-button>
                <el-collapse>
                  <el-collapse-item :title="表格数据.交易系统.详情弹窗.订单.订单标题" :disabled="表格数据.交易系统.详情弹窗.订单.订单禁用">
                    <el-table :data="表格数据.交易系统.详情弹窗.订单.订单列表" :show-header="false"><el-table-column>
                      <template slot-scope="scope2">
                          买家：{{scope2.row.买家}} ----- 时间：{{scope2.row.申请时间}} ----- 状态：{{scope2.row.申请状态}}<br>
                          备注
                          <el-input maxlength="50" placeholder="备注" v-model="scope2.row.申请备注" :disabled="表格数据.交易系统.详情弹窗.订单.备注修改禁用"></el-input>
                          评价
                          <el-input maxlength="50" placeholder="评价" v-model="scope2.row.购买评价" :disabled="表格数据.交易系统.详情弹窗.订单.评价修改禁用"></el-input>
                          <el-button type="primary" style="float: right" plain @click="订单功能按钮(scope2.row)" :disabled="表格数据.交易系统.详情弹窗.订单.订单按钮禁用">{{表格数据.交易系统.详情弹窗.订单.订单按钮}}</el-button>
                      </template>
                    </el-table-column></el-table>
                  </el-collapse-item>
                </el-collapse>
              </el-form>
            </el-scrollbar>
        </div>
      </el-dialog>
      <el-dialog title="修改密码" :visible.sync="修改密码弹窗显示" destroy-on-close :close-on-click-modal="false">
        <el-form ref="修改密码弹窗" :model="修改密码弹窗" :rules="修改密码rules" status-icon>
          <el-form-item prop="修改密码弹窗旧密码">
            <el-input v-model="修改密码弹窗.修改密码弹窗旧密码" placeholder="请输入旧密码" type="password"></el-input>
          </el-form-item>
          <el-form-item prop="修改密码弹窗新密码1">
            <el-input v-model="修改密码弹窗.修改密码弹窗新密码1" placeholder="请输入新密码" type="password"></el-input>
          </el-form-item>
          <el-form-item prop="修改密码弹窗新密码2">
            <el-input v-model="修改密码弹窗.修改密码弹窗新密码2" placeholder="请重复新密码" type="password"></el-input>
          </el-form-item>
        <el-button type="primary" @click="提交修改密码('修改密码弹窗')">修改密码</el-button>
      </el-form>
    </el-dialog>
    </el-main>
  </el-container>
</template>

<script>
export default {
  name: 'Market',
  data () {
    var checkPs = (rule, value, callback) => {
      if (value === '' || value === null) {
        callback(new Error('请再次输入新密码'))
      } else if (value !== this.修改密码弹窗.修改密码弹窗新密码1) {
        callback(new Error('两次输入新密码不一致!'))
      } else {
        callback()
      }
    }
    return {
      us: null,
      qx: null,
      lg: false,
      关闭审核: true,
      关闭管理: true,
      表格数据: {
        交易系统: {
          详情弹窗: {
            状态: '',
            禁用修改: false,
            显示: false,
            交易标题: '',
            卖家: '',
            创建时间: '',
            交易内容: '',
            按钮1: '购买',
            按钮2: '关闭',
            按钮1禁用: true,
            订单: {
              订单禁用: false,
              订单标题: '账单',
              订单列表: [],
              备注修改禁用: false,
              评价修改禁用: false,
              订单按钮禁用: true,
              订单按钮: '修改'
            }
          },
          单页显示选择: [10, 20, 50, 100],
          单页显示数量: 10,
          总条数: {},
          当前显示页数: {p1: 1, p2: 1, p3: 1, p4: 1, p5: 1, p6: 1},
          内容: {t1: null, t2: null, t3: null, t4: null, t5: null, t6: null}
        },
        审核系统: {
          内容: null,
          总条数: null,
          单页显示数量: 10,
          当前显示页数: 1
        },
        管理系统: {
          权限筛选: '全部',
          状态筛选: '全部',
          内容: [{用户: 'a', 创建时间: 'b', 权限: '管理员', 状态: '正常'}],
          总条数: null,
          单页显示数量: 10,
          当前显示页数: 1,
          权限选择: ['普通', '审核', '管理员'],
          状态选择: ['正常', '审核', '封禁']
        }
      },
      修改密码弹窗显示: false,
      修改密码弹窗: {
        修改密码弹窗旧密码: '',
        修改密码弹窗新密码1: '',
        修改密码弹窗新密码2: ''
      },
      修改密码rules: {
        修改密码弹窗旧密码: [{required: true, message: '请输入旧密码', trigger: 'blur'}, {min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur'}],
        修改密码弹窗新密码1: [{required: true, message: '请输入新密码', trigger: 'blur'}, {min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur'}],
        修改密码弹窗新密码2: [{validator: checkPs, trigger: 'blur'}, {min: 3, max: 10, message: '长度在 3 到 10 个字符', trigger: 'blur'}]
      }
    }
  },
  created () {
    this.getParams()
    if (!this.lg === true) {
      alert('登录信息失效，请重新登陆')
      this.$router.push('/Login')
    }
    this.刷新交易系统表()
    if (!this.关闭管理) {
      this.刷新管理系统表()
    }
  },
  methods: {
    getParams () {
      this.us = this.$route.params.us
      this.qx = this.$route.params.qx
      this.lg = this.$route.params.lg
      if (this.qx === '管理员') {
        this.关闭审核 = false
        this.关闭管理 = false
      }
      if (this.qx === '审核') {
        this.关闭审核 = false
      }
    },
    修改密码按钮 () {
      this.修改密码弹窗显示 = true
    },
    提交修改密码 (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.$axios.post('/resetpw', {us: this.us, ps: this.$md5(this.修改密码弹窗.修改密码弹窗旧密码), ps2: this.$md5(this.修改密码弹窗.修改密码弹窗新密码1)}).then(res => {
            if (res.data) {
              alert('操作成功')
            } else {
              alert('操作失败')
            }
            this.修改密码弹窗显示 = false
          }).catch(fail => {
            alert('网络错误')
          })
        } else {
          return false
        }
      })
    },
    重置密码 (item) {
      var temp = item
      temp.key = this.us
      this.$axios.post('/resetPs', temp).then(res => {
        var temp = item
        temp.us = this.us
        if (res.data) {
          alert('操作成功')
          this.刷新管理系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    保存用户 (item) {
      var temp = item
      temp.key = this.us
      this.$axios.post('/saveUser', temp).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新管理系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    新交易 () {
      this.表格数据.交易系统.详情弹窗.卖家 = this.us
      this.表格数据.交易系统.详情弹窗.创建时间 = '现在'
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = true
      this.表格数据.交易系统.详情弹窗.禁用修改 = false
      this.表格数据.交易系统.详情弹窗.状态 = '新交易'
      this.表格数据.交易系统.详情弹窗.交易标题 = ''
      this.表格数据.交易系统.详情弹窗.交易内容 = ''
      this.表格数据.交易系统.详情弹窗.按钮1 = '新建交易'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = false
      this.表格数据.交易系统.详情弹窗.按钮2 = '关闭'
      this.表格数据.交易系统.详情弹窗.订单.订单列表 = null
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    详情弹窗功能按钮 () {
      if (this.表格数据.交易系统.详情弹窗.状态 === '新交易') {
        this.添加出售()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情1') {
        this.添加订购()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情2') {
        this.修改出售()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情3') {
        this.修改出售()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情4') {
        this.删除订购()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情5') {
        this.删除订购()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '审核') {
        this.审核保存('公开')
      }
      this.表格数据.交易系统.详情弹窗.显示 = false
    },
    关闭详情弹窗 () {
      if (this.表格数据.交易系统.详情弹窗.状态 === '详情2') {
        this.删除出售()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情3') {
        this.删除出售()
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '审核') {
        this.审核保存('打回')
      }
      this.表格数据.交易系统.详情弹窗.显示 = false
    },
    订单功能按钮 (item) {
      if (this.表格数据.交易系统.详情弹窗.状态 === '详情2') {
        if (item.申请状态 === '完成') {
          alert('无效操作')
        } else {
          item.申请状态 = '完成'
          this.修改订购(item)
        }
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情4') {
        this.修改订购(item)
      } else if (this.表格数据.交易系统.详情弹窗.状态 === '详情6') {
        this.修改订购(item)
      }
      this.表格数据.交易系统.详情弹窗.显示 = false
    },
    添加出售 () {
      this.$axios.post('/addSellItem', {用户: this.表格数据.交易系统.详情弹窗.卖家, 创建时间: this.表格数据.交易系统.详情弹窗.创建时间, 交易标题: this.表格数据.交易系统.详情弹窗.交易标题, 交易内容: this.表格数据.交易系统.详情弹窗.交易内容, key: this.us}).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新交易系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    修改出售 () {
      this.$axios.post('/setSellItem', {用户: this.表格数据.交易系统.详情弹窗.卖家, 创建时间: this.表格数据.交易系统.详情弹窗.创建时间, 交易标题: this.表格数据.交易系统.详情弹窗.交易标题, 交易内容: this.表格数据.交易系统.详情弹窗.交易内容, key: this.us}).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新交易系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    审核保存 (value) {
      this.$axios.post('/setShenHeItem', {用户: this.表格数据.交易系统.详情弹窗.卖家, 创建时间: this.表格数据.交易系统.详情弹窗.创建时间, 交易标题: this.表格数据.交易系统.详情弹窗.交易标题, 交易内容: this.表格数据.交易系统.详情弹窗.交易内容, 交易状态: value, key: this.us}).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新交易系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    删除出售 () {
      this.$axios.post('/rmvSellItem', {用户: this.表格数据.交易系统.详情弹窗.卖家, 创建时间: this.表格数据.交易系统.详情弹窗.创建时间, key: this.us}).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新交易系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    添加订购 () {
      this.$axios.post('/addBuyItem', {卖家: this.表格数据.交易系统.详情弹窗.卖家, 创建时间: this.表格数据.交易系统.详情弹窗.创建时间, 买家: this.us, key: this.us}).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新交易系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    修改订购 (item) {
      this.$axios.post('/setBuyItem', {卖家: this.表格数据.交易系统.详情弹窗.卖家, 创建时间: this.表格数据.交易系统.详情弹窗.创建时间, 买家: item.买家, 申请时间: item.申请时间, 申请状态: item.申请状态, 申请备注: item.申请备注, 购买评价: item.购买评价, key: this.us}).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新交易系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    删除订购 () {
      this.$axios.post('/rmvBuyItem', {卖家: this.表格数据.交易系统.详情弹窗.卖家, 创建时间: this.表格数据.交易系统.详情弹窗.创建时间, 买家: this.表格数据.交易系统.详情弹窗.订单.订单列表[0].买家, 申请时间: this.表格数据.交易系统.详情弹窗.订单.订单列表[0].申请时间, key: this.us}).then(res => {
        if (res.data) {
          alert('操作成功')
          this.刷新交易系统表()
        } else {
          alert('操作失败')
        }
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    读取售卖记录 (item) {
      this.$axios.post('/getSellItem', {seller: item.用户, time: item.创建时间, us: this.us}).then(res => {
        this.表格数据.交易系统.详情弹窗.卖家 = res.data.用户
        this.表格数据.交易系统.详情弹窗.创建时间 = res.data.创建时间
        this.表格数据.交易系统.详情弹窗.交易标题 = res.data.交易标题
        this.表格数据.交易系统.详情弹窗.交易内容 = res.data.交易内容
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    读取售卖记录2 (item) {
      this.$axios.post('/getSellItem', {seller: item.卖家, time: item.创建时间, us: this.us}).then(res => {
        this.表格数据.交易系统.详情弹窗.卖家 = res.data.用户
        this.表格数据.交易系统.详情弹窗.创建时间 = res.data.创建时间
        this.表格数据.交易系统.详情弹窗.交易标题 = res.data.交易标题
        this.表格数据.交易系统.详情弹窗.交易内容 = res.data.交易内容
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    读取订单记录_单 (item) {
      this.$axios.post('/getBuyItem', {seller: item.卖家, time: item.创建时间, buyer: item.买家, time2: item.申请时间, us: this.us}).then(res => {
        this.表格数据.交易系统.详情弹窗.订单.订单列表 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    读取订单记录_列1 (item) {
      this.$axios.post('/getBuyItemList1', {seller: item.用户, time: item.创建时间, us: this.us}).then(res => {
        this.表格数据.交易系统.详情弹窗.订单.订单列表 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    读取订单记录_列2 (item) {
      this.$axios.post('/getBuyItemList2', {seller: item.用户, time: item.创建时间, us: this.us}).then(res => {
        this.表格数据.交易系统.详情弹窗.订单.订单列表 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    读取订单记录_列3 (item) {
      this.$axios.post('/getBuyItemList3', {seller: item.用户, time: item.创建时间, us: this.us}).then(res => {
        this.表格数据.交易系统.详情弹窗.订单.订单列表 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    查看详情J1 (item) {
      this.读取售卖记录(item)
      this.读取订单记录_列1(item)
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = false
      this.表格数据.交易系统.详情弹窗.禁用修改 = true
      this.表格数据.交易系统.详情弹窗.状态 = '详情1'
      this.表格数据.交易系统.详情弹窗.订单.备注修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮 = '----'
      this.表格数据.交易系统.详情弹窗.按钮1 = '添加订单'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = false
      this.表格数据.交易系统.详情弹窗.按钮2 = '关闭'
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    查看详情J2 (item) {
      this.读取售卖记录(item)
      this.读取订单记录_列2(item)
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = false
      this.表格数据.交易系统.详情弹窗.禁用修改 = false
      this.表格数据.交易系统.详情弹窗.状态 = '详情2'
      this.表格数据.交易系统.详情弹窗.订单.备注修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = false
      this.表格数据.交易系统.详情弹窗.订单.订单按钮 = '完成'
      this.表格数据.交易系统.详情弹窗.按钮1 = '修改信息'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = false
      this.表格数据.交易系统.详情弹窗.按钮2 = '结束出售'
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    查看详情J3 (item) {
      this.读取售卖记录(item)
      this.读取订单记录_列3(item)
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = false
      this.表格数据.交易系统.详情弹窗.禁用修改 = false
      this.表格数据.交易系统.详情弹窗.状态 = '详情3'
      this.表格数据.交易系统.详情弹窗.订单.备注修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮 = '----'
      this.表格数据.交易系统.详情弹窗.按钮1 = '重新发送'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = false
      this.表格数据.交易系统.详情弹窗.按钮2 = '删除出售'
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    查看详情J4 (item) {
      this.读取售卖记录2(item)
      this.读取订单记录_单(item)
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = false
      this.表格数据.交易系统.详情弹窗.禁用修改 = true
      this.表格数据.交易系统.详情弹窗.状态 = '详情4'
      this.表格数据.交易系统.详情弹窗.订单.备注修改禁用 = false
      this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = false
      this.表格数据.交易系统.详情弹窗.订单.订单按钮 = '备注'
      this.表格数据.交易系统.详情弹窗.按钮1 = '取消订单'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = false
      this.表格数据.交易系统.详情弹窗.按钮2 = '关闭'
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    查看详情J5 (item) {
      this.读取售卖记录2(item)
      this.读取订单记录_单(item)
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = false
      this.表格数据.交易系统.详情弹窗.禁用修改 = true
      this.表格数据.交易系统.详情弹窗.状态 = '详情5'
      this.表格数据.交易系统.详情弹窗.订单.备注修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮 = '----'
      this.表格数据.交易系统.详情弹窗.按钮1 = '取消订单'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = false
      this.表格数据.交易系统.详情弹窗.按钮2 = '关闭'
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    查看详情J6 (item) {
      this.读取售卖记录2(item)
      this.读取订单记录_单(item)
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = false
      this.表格数据.交易系统.详情弹窗.禁用修改 = true
      this.表格数据.交易系统.详情弹窗.状态 = '详情6'
      this.表格数据.交易系统.详情弹窗.订单.备注修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮 = '评论'
      this.表格数据.交易系统.详情弹窗.按钮1 = '--------'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = true
      this.表格数据.交易系统.详情弹窗.按钮2 = '关闭'
      if (item.买家 === this.us) {
        this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = false
        this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = false
      }
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    查看详情S (item) {
      this.读取售卖记录(item)
      this.表格数据.交易系统.详情弹窗.订单.订单禁用 = true
      this.表格数据.交易系统.详情弹窗.禁用修改 = true
      this.表格数据.交易系统.详情弹窗.状态 = '审核'
      this.表格数据.交易系统.详情弹窗.订单.备注修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.评价修改禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮禁用 = true
      this.表格数据.交易系统.详情弹窗.订单.订单按钮 = '----'
      this.表格数据.交易系统.详情弹窗.按钮1 = '通过'
      this.表格数据.交易系统.详情弹窗.按钮1禁用 = false
      this.表格数据.交易系统.详情弹窗.按钮2 = '打回'
      this.表格数据.交易系统.详情弹窗.显示 = true
    },
    刷新审核系统表 () {
      this.$axios.post('/getShenHeSize', {us: this.us}).then(res => {
        this.表格数据.审核系统.总条数 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
      this.$axios.post('/getShenHeTable', {show: (this.表格数据.审核系统.当前显示页数 - 1), page: this.表格数据.审核系统.单页显示数量, us: this.us}).then(res => {
        this.表格数据.审核系统.内容 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新交易系统表 () {
      this.刷新总条数()
      this.刷新J1()
      this.刷新J2()
      this.刷新J3()
      this.刷新J4()
      this.刷新J5()
      this.刷新J6()
      if (!this.关闭审核) {
        this.刷新审核系统表()
      }
    },
    刷新管理系统表 () {
      this.$axios.post('/getUserSize', {us: this.us, 权限: this.表格数据.管理系统.权限筛选, 状态: this.表格数据.管理系统.状态筛选}).then(res => {
        this.表格数据.管理系统.总条数 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
      this.$axios.post('/getUserList', {us: this.us, 权限: this.表格数据.管理系统.权限筛选, 状态: this.表格数据.管理系统.状态筛选}).then(res => {
        this.表格数据.管理系统.内容 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新总条数 () {
      this.$axios.post('/getTradeSize', {us: this.us}).then(res => {
        this.表格数据.交易系统.总条数 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新J1 () {
      this.$axios.post('/getTradeTable1', {show: (this.表格数据.交易系统.当前显示页数.p1 - 1), page: this.表格数据.交易系统.单页显示数量, us: this.us}).then(res => {
        this.表格数据.交易系统.内容.t1 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新J2 () {
      this.$axios.post('/getTradeTable2', {show: (this.表格数据.交易系统.当前显示页数.p2 - 1), page: this.表格数据.交易系统.单页显示数量, us: this.us}).then(res => {
        this.表格数据.交易系统.内容.t2 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新J3 () {
      this.$axios.post('/getTradeTable3', {show: (this.表格数据.交易系统.当前显示页数.p3 - 1), page: this.表格数据.交易系统.单页显示数量, us: this.us}).then(res => {
        this.表格数据.交易系统.内容.t3 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新J4 () {
      this.$axios.post('/getTradeTable4', {show: (this.表格数据.交易系统.当前显示页数.p4 - 1), page: this.表格数据.交易系统.单页显示数量, us: this.us}).then(res => {
        this.表格数据.交易系统.内容.t4 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新J5 () {
      this.$axios.post('/getTradeTable5', {show: (this.表格数据.交易系统.当前显示页数.p5 - 1), page: this.表格数据.交易系统.单页显示数量, us: this.us}).then(res => {
        this.表格数据.交易系统.内容.t5 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    刷新J6 () {
      this.$axios.post('/getTradeTable6', {show: (this.表格数据.交易系统.当前显示页数.p6 - 1), page: this.表格数据.交易系统.单页显示数量, us: this.us}).then(res => {
        this.表格数据.交易系统.内容.t6 = res.data
      }).catch(fail => {
        alert('网络错误')
        this.$router.push('/Login')
      })
    },
    取标签 (input) {
      if (input === '公开') {
        return 'success'
      } else if (input === '审核') {
        return 'warning'
      } else if (input === '打回') {
        return 'danger'
      } else if (input === '失效') {
        return 'info'
      } else if (input === '完成') {
        return 'success'
      } else if (input === '申请') {
        return 'primary'
      } else if (input === '封禁') {
        return 'info'
      } else if (input === '正常') {
        return 'success'
      } else if (input === '普通') {
        return 'primary'
      } else if (input === '管理员') {
        return 'success'
      }
      return ''
    },
    退出登录 () {
      this.$router.push('/Login')
    },
    更改单页显示条数 (val) {
      this.表格数据.交易系统.单页显示数量 = val
      this.刷新交易系统表()
    },
    更改单页显示条数S (val) {
      this.表格数据.审核系统.单页显示数量 = val
      this.刷新审核系统表()
    },
    更改单页显示条数G (val) {
      this.表格数据.管理系统.单页显示数量 = val
      this.刷新管理系统表()
    },
    跳转到页J1 (val) {
      this.表格数据.交易系统.当前显示页数.p1 = val
      this.刷新J1()
    },
    跳转到页J2 (val) {
      this.表格数据.交易系统.当前显示页数.p2 = val
      this.刷新J2()
    },
    跳转到页J3 (val) {
      this.表格数据.交易系统.当前显示页数.p3 = val
      this.刷新J3()
    },
    跳转到页J4 (val) {
      this.表格数据.交易系统.当前显示页数.p4 = val
      this.刷新J4()
    },
    跳转到页J5 (val) {
      this.表格数据.交易系统.当前显示页数.p5 = val
      this.刷新J5()
    },
    跳转到页J6 (val) {
      this.表格数据.交易系统.当前显示页数.p6 = val
      this.刷新J6()
    },
    跳转到页S (val) {
      this.表格数据.审核系统.当前显示页数 = val
      this.刷新审核系统表()
    },
    跳转到页G (val) {
      this.表格数据.管理系统.当前显示页数 = val
      this.刷新管理系统表()
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .el-header, .el-footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-aside {
    background-color: #D3DCE6;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 60px;
  }
  .white-space {
    white-space:pre
  }
</style>
