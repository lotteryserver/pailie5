# pailie5
体育彩票排列5,体彩排列五算法源代码


部署教程和源码备份下载地址 链接：https://pan.baidu.com/s/1gWQckRKM-pY7uCiujZB54g?pwd=4bf7 提取码：4bf7

仿中国体育擦彩票排列5源码 前端代码如下： 
<template>
	<view class="box">

		<cmd-nav-bar back title="排列5" font-color="#fff" background-color="#FF3F43" right-text="排列5开奖"
			@rightText="rightBtn">
		</cmd-nav-bar>
		<div style="height:100%">
			<p class="fc_index">第{{issueNo}}期，21:40开奖</p>
			<div class="fc">
				<view
					style="display: flex;justify-content: space-between;align-items: center;width: 95%;margin: 0 auto;">
					<p class="tips"><span class="shake"></span>选择<span>5</span>个号码，中奖<span>100000</span>元
					</p>
					<u-checkbox-group @change="checkboxChange" size="15" shape="square" placement="column"
						style="margin-left: 20px;">
						<u-checkbox labelSize="14" activeColor="#FF3F43" :label="'显示遗漏'">
						</u-checkbox>
					</u-checkbox-group>
				</view>
				<ul>
					<p>万位</p>
					<li @click="check(1,1,index)" v-for="(item,index) in myriad" :class="item.active?'active':''">
						{{item.num}}
						<view v-if="omitData.record!=undefined&&omiIsShow"
							style="color: #A5A5A5;font-size: 13px;margin-top: -8px;">
							{{omitData.record[index]}}
						</view>
					</li>
				</ul>
				<u-divider></u-divider>
				<ul>
					<p>千位</p>
					<li @click="check(1,2,index)" v-for="(item,index) in kilo" :class="item.active?'active':''">
						{{item.num}}
						<view v-if="omitData.record!=undefined&&omiIsShow"
							style="color: #A5A5A5;font-size: 13px;margin-top: -8px;">
							{{omitData.record[index+10]}}
						</view>
					</li>
				</ul>
				<u-divider></u-divider>
				<ul>
					<p>百位</p>
					<li @click="check(1,3,index)" v-for="(item,index) in bai" :class="item.active?'active':''">
						{{item.num}}
						<view v-if="omitData.record!=undefined&&omiIsShow"
							style="color: #A5A5A5;font-size: 13px;margin-top: -8px;">
							{{omitData.record[index+20]}}
						</view>
					</li>
				</ul>
				<u-divider></u-divider>
				<ul>
					<p>十位</p>
					<li @click="check(1,4,index)" v-for="(item,index) in shi" :class="item.active?'active':''">
						{{item.num}}
						<view v-if="omitData.record!=undefined&&omiIsShow"
							style="color: #A5A5A5;font-size: 13px;margin-top: -8px;">
							{{omitData.record[index+30]}}
						</view>
					</li>
				</ul>
				<u-divider></u-divider>
				<ul>
					<p>个位</p>
					<li @click="check(1,5,index)" v-for="(item,index) in ge" :class="item.active?'active':''">
						{{item.num}}
						<view v-if="omitData.record!=undefined&&omiIsShow"
							style="color: #A5A5A5;font-size: 13px;margin-top: -8px;">
							{{omitData.record[index+40]}}
						</view>
					</li>
				</ul>
			</div>
			<Acount :total="total" :acount="acount" @clear="clear" @confirm="sure" />
		</div>

	</view>
</template>
<script>
	import {
		getIssueNo
	} from '@/api/pailie.js'
	import {
		getOmitByType
	} from '@/api/omit.js'
	import Acount from '../common/Acount'
	export default {
		data() {
			return {
				total: 0,
				acount: 0,
				issueNo: "",
				omiIsShow:false,
				ge: [{
						num: 0,
						active: false
					}, {
						num: 1,
						active: false
					}, {
						num: 2,
						active: false
					}, {
						num: 3,
						active: false
					}, {
						num: 4,
						active: false
					},
					{
						num: 5,
						active: false
					}, {
						num: 6,
						active: false
					}, {
						num: 7,
						active: false
					}, {
						num: 8,
						active: false
					}, {
						num: 9,
						active: false
					}
				],
				shi: [{
						num: 0,
						active: false
					}, {
						num: 1,
						active: false
					}, {
						num: 2,
						active: false
					}, {
						num: 3,
						active: false
					}, {
						num: 4,
						active: false
					},
					{
						num: 5,
						active: false
					}, {
						num: 6,
						active: false
					}, {
						num: 7,
						active: false
					}, {
						num: 8,
						active: false
					}, {
						num: 9,
						active: false
					}
				],
				bai: [{
						num: 0,
						active: false
					}, {
						num: 1,
						active: false
					}, {
						num: 2,
						active: false
					}, {
						num: 3,
						active: false
					}, {
						num: 4,
						active: false
					},
					{
						num: 5,
						active: false
					}, {
						num: 6,
						active: false
					}, {
						num: 7,
						active: false
					}, {
						num: 8,
						active: false
					}, {
						num: 9,
						active: false
					}
				],
				kilo: [{
						num: 0,
						active: false
					}, {
						num: 1,
						active: false
					}, {
						num: 2,
						active: false
					}, {
						num: 3,
						active: false
					}, {
						num: 4,
						active: false
					},
					{
						num: 5,
						active: false
					}, {
						num: 6,
						active: false
					}, {
						num: 7,
						active: false
					}, {
						num: 8,
						active: false
					}, {
						num: 9,
						active: false
					}
				],
				myriad: [{
						num: 0,
						active: false
					}, {
						num: 1,
						active: false
					}, {
						num: 2,
						active: false
					}, {
						num: 3,
						active: false
					}, {
						num: 4,
						active: false
					},
					{
						num: 5,
						active: false
					}, {
						num: 6,
						active: false
					}, {
						num: 7,
						active: false
					}, {
						num: 8,
						active: false
					}, {
						num: 9,
						active: false
					}
				],
				gearr: [],
				shiarr: [],
				baiarr: [],
				kiloarr: [],
				myriadarr: [],
				omitData: {}
			}
		},
		components: {
			Acount
		},
		onLoad() {
			this.init()
		},
		methods: {
			checkboxChange(item) {
				if (item[0] == "") {
					this.omiIsShow=true;
				}else{
					this.omiIsShow=false;
				}
			},
			init() {
				getIssueNo("4").then(res => {
					this.issueNo = res.stageNumber
				})
				getOmitByType("4").then(res => {
					this.omitData = res
					this.omitData.record = res.record.split(",")
				})
			},
			rightBtn() {
				uni.navigateTo({
					url: "/pages/pailie5/openPrize"
				})
			},
			check(type, wei = 0, index) {
				switch (type) {
					case 1:
						if (wei == 1) {
							this.myriad[index].active = !this.myriad[index].active;
						};
						if (wei == 2) {
							this.kilo[index].active = !this.kilo[index].active;
						};
						if (wei == 3) {
							this.bai[index].active = !this.bai[index].active;
						};
						if (wei == 4) {
							this.shi[index].active = !this.shi[index].active;
						};
						if (wei == 5) {
							this.ge[index].active = !this.ge[index].active;
						};
						this.gearr = this.ge.filter(v => {
							return v.active
						})
						this.shiarr = this.shi.filter(v => {
							return v.active
						})
						this.baiarr = this.bai.filter(v => {
							return v.active
						})
						this.kiloarr = this.kilo.filter(v => {
							return v.active
						})
						this.myriadarr = this.myriad.filter(v => {
							return v.active
						})
						this.acount = this.globalUtil.math(this.myriadarr.length, 1) * this.globalUtil.math(this.kiloarr
							.length, 1) * this.globalUtil.math(this.baiarr.length, 1) * this.globalUtil.math(this
							.shiarr
							.length, 1) * this.globalUtil.math(this.gearr.length, 1)
						break;
				}
				this.total = this.acount * 2;
			},
			clear() {
				this.ge.map(v => {
					v.active = false;
				});
				this.shi.map(v => {
					v.active = false;
				});
				this.bai.map(v => {
					v.active = false;
				});
				this.kilo.map(v => {
					v.active = false;
				});
				this.myriad.map(v => {
					v.active = false;
				});
				this.total = 0
				this.acount = 0
				this.gearr = []
				this.shiarr = []
				this.baiarr = []
				this.kiloarr = []
				this.myriadarr = []
			},
			//机选
			randomSelect() {
				this.clear()
				let numberArr = this.globalUtil.randomFromZero(10, 5);
				this.myriad[numberArr[0]].active = true
				this.kilo[numberArr[1]].active = true
				this.bai[numberArr[2]].active = true
				this.shi[numberArr[3]].active = true
				this.ge[numberArr[4]].active = true
				this.shiarr = this.shi.filter(v => {
					return v.active
				})
				this.baiarr = this.bai.filter(v => {
					return v.active
				})
				this.gearr = this.ge.filter(v => {
					return v.active
				})
				this.kiloarr = this.kilo.filter(v => {
					return v.active
				})
				this.myriadarr = this.myriad.filter(v => {
					return v.active
				})
				this.acount = this.globalUtil.math(this.myriadarr.length, 1) * this.globalUtil.math(this.kiloarr
					.length, 1) * this.globalUtil.math(this.baiarr.length, 1) * this.globalUtil.math(this
					.shiarr
					.length, 1) * this.globalUtil.math(this.gearr.length, 1)
				this.total = this.acount * 2;
			},
			sure() {
				if (this.total == 0) {
					this.randomSelect();
					return;
				}
				//随机数id用户传到购物车进行去重处理
				let uid = Math.ceil(Math.random() * 9999999999999999)
				let data = {
					uid: uid,
					mode: 0,
					notes: this.acount,
					total: this.total,
					individual: this.gearr.map(v => {
						return v.num
					}),
					ten: this.shiarr.map(v => {
						return v.num
					}),
					hundred: this.baiarr.map(v => {
						return v.num
					}),
					kilo: this.kiloarr.map(v => {
						return v.num
					}),
					myriad: this.myriadarr.map(v => {
						return v.num
					})

				}
				uni.navigateTo({
					url: "/pages/pailie5/buyShoppingCar?obj=" + encodeURIComponent(JSON.stringify(data)),
					animationType: 'pop-in',
					animationDuration: 200
				})
			},
		},
	}
</script>
<style scoped>
	/deep/.cmd-nav-bar-right-text {
		font-size: 16px !important;
	}

	.tips {
		padding: 20rpx;
		color: #999;
		font-size: 28rpx;
	}

	.tips span {
		color: #FF3F43;
	}

	.fc {
		margin-bottom: 30rpx;
	}

	.fc ul {
		margin-top: 12rpx;
		padding-left: 36rpx;
	}

	.fc ul p {
		height: 50rpx;
		line-height: 50rpx;
		color: #fff;
		background: #FF3F43;
		width: 100rpx;
		font-size: 30rpx;
		padding-left: 20rpx;
		margin-left: -36rpx;
		border-top-right-radius: 30rpx;
		border-bottom-right-radius: 30rpx;
	}

	.fc ul li {
		display: inline-block;
		width: 74rpx;
		color: #FF3F43;
		background: #fff;
		height: 74rpx;
		text-align: center;
		line-height: 74rpx;
		font-size: 30rpx;
		border: 1px solid #e2e2e2;
		border-radius: 50%;
		margin: 18rpx
	}

	.fc ul li.active {
		background: #FF3F43;
		color: #fff;
	}

	.fc_index {
		padding-top: 40rpx;
		height: 60rpx;
		line-height: 30rpx;
		color: #999;
		font-size: 28rpx;
		background: #fff;
		text-align: center;
	}
</style>
前端处理代码如下：

<template>
	<view class="box">

		<nav-bar :title="'排列5'" :back="true"></nav-bar>
		<div class="shoppingCar_wrap">
			<div class="shoppingCar_content">
				<div class="shoppingCar_add">
					<div class="add_once" @tap="random">+机选1注</div>
					<div class="add_back" @tap="back">+继续选号</div>
					<div class="add_back" @tap="clean">+清空列表</div>
				</div>
				<div class="shoppingCar_added">
					<div class="added_selected" v-for="arr in placeData">
						<div class="selected_left">
							<div class="selected_text">
								<div class="selected_num">
									<div class="content" v-for="a in arr.myriad">
										<p>{{a}}</p>
									</div>
									<span class="vertical" v-if="arr.myriad!=null">|</span>

									<div class="content" v-for="a in arr.kilo">
										<p>{{a}}</p>
									</div>
									<span class="vertical" v-if="arr.kilo!=null">|</span>
									
									<div class="content" v-for="a in arr.hundred">
										<p>{{a}}</p>
									</div>
									<span class="vertical" v-if="arr.hundred!=null">|
									</span>
									<div class="content" v-for="b in arr.ten">
										<p>{{b}}</p>
									</div>
									<span class="vertical" v-if="arr.ten!=null">|
									</span>
									<div class="content" v-for="c in arr.individual">
										<p>{{c}}</p>
									</div>
								</div>
								<div class="selected_count">
									{{arr.notes}}注 {{arr.total}}元
								</div>
							</div>
						</div>
						<u-icon @tap="del(arr.uid)" name="trash" size="26" color="#909399"></u-icon>
					</div>
					<div class="added_rule">
						<div class="rule_left">
							<span>购买即同意《委托投注协议》</span>
						</div>
					</div>
				</div>
			</div>
			<div class="shoppingCar_footer">
				<view style="display: flex; justify-content: center;align-items: center;">
					投<u-number-box iconStyle="color: #FF3F43" integer inputWidth="70" @change="numberChange">
					</u-number-box>倍
				</view>
				<div class="footer_bottom">
					<div class="bottom_left">
						共 <b>{{acount}}</b>注 <b>{{total}}</b>元
					</div>
					<div class="bottom_right">
						<span @tap="() => confirmIsShow = true">下一步</span>
					</div>
				</div>
			</div>
		</div>
		<u-modal title="投注确认" :show="confirmIsShow" :zoom="false" confirmText="投注" showCancelButton
			confirmColor="#FF3F43" @confirm="betting" @cancel="() => confirmIsShow = false">
			<view class="tip">
				<p>[排列5]</p>
				<p>第{{issueNo}}期</p>
				<p>共{{acount}}注，您需要支付{{total}}元</p>
			</view>
		</u-modal>

	</view>
</template>

<script>
	import {
		place,
		getIssueNo
	} from '@/api/pailie.js'
	export default {
		data() {
			return {
				confirmIsShow: false,
				placeData: [],
				total: 0,
				acount: 0,
				times: 1,
				issueNo: ""
			}
		},
		onLoad(option) {
			if (option.obj != undefined) {
				let obj = JSON.parse(decodeURIComponent(option.obj));
				this.calculation(obj);
			}
			//当前期号
			getIssueNo("4").then(res => {
				this.issueNo = res.stageNumber
			})
		},
		methods: {
			//投注
			betting() {
				uni.showLoading();
				let data = uni.getStorageSync('pailie5');
				if (data.length <= 0) {
					uni.showToast({
						title: '至少选择一注',
						icon: 'none'
					});
					return;
				}
				if (this.total < 10) {
					uni.showToast({
						title: '下单金额最低10元起投',
						icon: 'none'
					});
					return;
				}
				//往数组中添加倍数新字段
				data.forEach(item => {
					this.$set(item, 'times', this.times)
					delete item['total']
					delete item['uid']
				})
				place(data, "4").then(res => {
					if (res.success) {
						uni.showToast({
							title: '下单成功',
							icon: 'none'
						});
						//标识为已经下单了
						uni.setStorageSync('isPay', true);
						this.clean();
						this.confirmIsShow = false;
						setTimeout(function() {
							uni.hideLoading();
						}, 500);
						uni.navigateTo({
							url: "/pages/order/lotteryOrderDetails?id=" + res.id,
							animationType: 'pop-in',
							animationDuration: 200
						})
					}
				})
			},
			//计算
			calculation(obj) {
				let data = uni.getStorageSync('pailie5');
				let isRepeat = false
				if (data.length > 0) {
					data.map(item => {
						//如果有重复进行标记
						if (item.uid == obj.uid) {
							isRepeat = true;
							return;
						}
					})
					//根据标记去重处理
					if (!isRepeat) {
						//如果不是重复的继续叠加
						data.unshift(obj)
						uni.setStorageSync("pailie5", data)
					}
					//赋值
					this.placeData = data
					//计算总价和总注数
					data.map(item => {
						this.total += item.total
						this.acount += item.notes
					})
				} else {
					//第一次为空的时候写入到本地缓存
					this.placeData.push(obj)
					uni.setStorageSync("pailie5", this.placeData)
					this.total = obj.total;
					this.acount = obj.notes;
				}
			},
			//机选
			random() {
				this.total = 0;
				this.acount = 0;
				let uid = Math.ceil(Math.random() * 9999999999999999)
				let arr = this.globalUtil.randomFromZero(10, 5);
				let obj = {
					uid: uid,
					mode: 0,
					notes: 1,
					total: 2,
					individual: [arr[0]],
					ten: [arr[1]],
					hundred: [arr[2]],
					kilo: [arr[3]],
					myriad: [arr[4]]
				}
				this.calculation(obj);
			},
			//删除
			del(uid) {
				let data = uni.getStorageSync('pailie5');
				//重新计算总价和总注数
				data.map(item => {
					if (item.uid == uid) {
						this.total -= item.total
						this.acount -= item.notes
					}
				})
				//删除数据
				data = data.filter((item) => {
					return item.uid != uid;
				});
				//重新赋值
				this.placeData = data
				//写入缓存
				uni.setStorageSync("pailie5", data)
			},
			numberChange(item) {
				this.total = this.acount * item.value * 2
				this.times = item.value;
			},
			back() {
				uni.navigateTo({
					url: "/pages/pailie5/pailie5",
					animationType: 'pop-in',
					animationDuration: 200
				})
			},
			//清空
			clean() {
				uni.removeStorageSync("pailie5")
				this.placeData = []
				this.total = 0;
				this.acount = 0;
			}
		},
	}
</script>

<style scoped lang="scss">
	.vertical {
		color: #848484;
		padding: 0 10rpx;
	}

	.content {
		width: 25px;
		height: 25px;
		background-color: #FF3F43;
		border-radius: 50%;
		display: inline-block;
		margin-right: 2px;

		p {
			width: 25px;
			height: 25px;
			color: #fff;
			text-align: center;
			line-height: 25px;
			font-size: 16px;
		}
	}

	.tip {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;

		p {
			margin-top: 8rpx;
			color: #606266;
			font-size: 16px;
		}
	}

	.shoppingCar_wrap {
		.shoppingCar_content {
			.shoppingCar_add {
				margin-bottom: 2.26667vmin;
				font-size: 3.73333vmin;
				padding: 0 3.33333vmin;
				display: flex;
				align-items: center;
				justify-content: space-between;

				div {
					width: 48%;
					background-color: white;
					height: 11.46667vmin;
					display: flex;
					justify-content: center;
					align-items: center;
					color: #666;
				}
			}

			.shoppingCar_added {
				box-sizing: border-box;
				margin: 0 26rpx;

				.added_rule {
					box-sizing: border-box;
					font-size: 3.46667vmin;
					height: 12.53333vmin;
					width: 100%;
					background-color: white;
					color: #999;
					display: flex;
					align-items: center;
					justify-content: space-between;
					padding: 0 4.4vmin;
				}

				.added_selected {
					background-color: white;
					padding: 2.66667vmin;
					box-sizing: border-box;
					border-bottom: 1px solid #e6e6e6;
					display: flex;
					align-items: center;
					justify-content: space-between;

					.selected_left {
						display: flex;
						align-items: center;
						justify-content: center;

						.selected_text {

							.selected_num {
								color: #FF5562;
								font-size: 5.33333vmin;
								margin-bottom: 1.8vmin;
							}

							.selected_count {
								font-size: 3.46667vmin;
								color: #999;
							}
						}
					}
				}
			}
		}

		.shoppingCar_footer {
			width: 100%;
			position: fixed;
			bottom: 0;
			left: 0;
			color: #8f9090;
			background-color: white;

			.footer_bottom {
				box-sizing: border-box;
				width: 100%;
				display: flex;
				align-items: center;
				justify-content: space-between;
				height: 13.33333vmin;
				padding-left: 2.66667vmin;

				.bottom_left {
					color: #333333;
					font-size: 4vmin;

					b {
						color: #FF5562;
					}
				}

				.bottom_right {
					/*border: none;*/
					text-align: center;
					background: #FF3F43;
					color: #FFFFFF;
					font-size: 4.8vmin;
					width: 28.53333vmin;
					border-radius: 4px;
					height: 100%;
					display: flex;
					align-items: center;
					justify-content: center;
				}
			}
		}
	}
</style>

API接口代码：
import request from '@/util/ajax'


/**
 * 排列下单
 * @param {Object} data
 */
export function place(data,type) {
	return request({
		url: '/app/permutation/place/'+type,
		method: 'post',
		data
	})
}

/**
 * 历史排列开奖记录
 */
export function record(type) {
	return request({
		url: '/app/permutation/record/'+type,
		method: 'get',
	})
}

/**
 * 获取排列期号接口
 */
export function getIssueNo(type) {
	return request({
		url: '/app/permutation/issue/'+type,
		method: 'get',
	})
}
