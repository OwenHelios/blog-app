<!-- 个人中心 -->
<template>
	<view class="components-theme">
		<!-- 顶部背景 -->
		<view class='UCenter-bg' :style="'background-image: url(' + pic[topBackGroupImageIndex].link + ');margin-top:' + CustomBar + 'px;'">
			<view class='space' v-show="spaceShow">
				<view class="stars ">
					<view class="star "></view>
					<view class="star pink "></view>
					<view class="star blue "></view>
					<view class="star yellow "></view>
				</view>
			</view>

			<block>
				<view class='text-center' @click="goMedal">
					<view class="cu-avatar2 round xl margin-right-sm shadow-blur-lg bg-img open-data" style="overflow: hidden;">
						<open-data type="userAvatarUrl"></open-data>
					</view>
					<view class="padding text-blue text-xl text-bold">
						你好，<open-data type="userNickName"></open-data>
					</view>

				</view>
			</block>

			<image src='https://cdn.nlark.com/yuque/0/2019/gif/280373/1570670848649-assets/web-upload/3dbaa72a-062b-470f-9b9d-058ff8f85ab8.gif'
			 mode='scaleToFill' class='gif-wave'></image>
		</view>

		<block>
			<view class='padding flex text-center text-grey bg-white shadow-warp-my'>
				<view class='flex flex-sub flex-direction solid-right'>
					<view class="text-xxl text-orange">11.6k+</view>
					<view class="margin-top-sm">
						<text class='cuIcon-hot'></text> 访客</view>
				</view>
				<view class='flex flex-sub flex-direction solid-right'>
					<view class="text-xxl text-blue">8.6k</view>
					<view class="margin-top-sm">
						<text class='cuIcon-share'></text> 分享</view>
				</view>
				<view class='flex flex-sub flex-direction'>
					<view class="text-xxl text-red">2.6k+</view>
					<view class="margin-top-sm">
						<text class='cuIcon-like'></text> 点赞</view>
				</view>
			</view>


			<view class="cu-list menu card-menu margin-top-lg margin-bottom-sm shadow-shop bg-white text-black my-radius sm-border">
				<view class="cu-item" @tap="showModal" data-target="Modal">
					<view class='content'>
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>主题切换</text>
					</view>
					<view class='action'>
						<view class="cu-capsule radius">
							<view class='cu-tag bg-gradual-blue'>
								<view style="clear: both;"></view>
							</view>
							<view class="cu-tag line-blue">
								{{picName}}
							</view>
						</view>
					</view>
				</view>

				<view class="cu-item " @click="mentalTest">
					<button class='content cu-btn'>
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>答题测试</text>
					</button>
					<view class="action">
						<view class="cu-tag round bg-orange light">技术</view>
						<view class="cu-tag round bg-olive light">性格</view>
						<view class="cu-tag round bg-blue light">星座</view>
					</view>
				</view>

				
				<view class="cu-item">
					<button class='content cu-btn' open-type="share">
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>分享小程序</text>
					</button>
				</view>
				
				<view class="cu-item" @click="playVideo">
					<button class='content cu-btn'>
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>支持作者</text>
					</button>
					<view class="action">
						<text class="text-xs text-orange">不需要打钱！</text>
						<text class="text-xs text-grey">看看广告就很感谢啦～</text>
					</view>
				</view>
				
				<view class="cu-item">
					<button class='content cu-btn' @tap="showGitee" data-target="ModalGitee">
						<image style="border-radius: 50rpx;" src='https://zhoukaiwen.com/img/icon/gitee_logo.jpeg' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>下载小程序源码</text>
					</button>
				</view>

			</view>

			<view class="cu-list menu card-menu margin-top-lg margin-bottom-lg shadow-shop bg-white text-black my-radius sm-border">

				<view class="cu-item ">
					<button class='content cu-btn' open-type="contact">
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>项目需求</text>
					</button>
				</view>

				<view class="cu-item" @click="callPhoneNumber" data-number="18629591093">
					<view class='content'>
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>技术支持</text>
					</view>
					<view class="action">
						<view class="cu-tag round bg-blue light">186 2959 1093</view>
					</view>
				</view>

				<view class="cu-item">
					<button class='content cu-btn' open-type="feedback">
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>问题反馈</text>
					</button>
				</view>
				<view class="cu-item">
					<button class='content cu-btn' @click="goAboutMe">
						<image src='/static/home.png' class='png' mode='aspectFit'></image>
						<text class='text-lg margin-sm'>关于作者</text>
					</button>
				</view>
			</view>

		</block>
		
		<!-- Gitee弹窗 -->
		<view class="cu-modal" :class="modalName=='ModalGitee'?'show':''">
			<view class="cu-dialog">
				<view class="cu-bar bg-white justify-end">
					<view class="content">Gitee访问</view>
					<view class="action" @tap="hideModal">
						<text class="cuIcon-close text-red"></text>
					</view>
				</view>
				<view class="padding-xl">
					<image src="https://zhoukaiwen.com/img/icon/qdpzGitee.png" mode="widthFix" style="width: 100%;"></image>
					<p class="giteeClass" @click="getGitee">https://gitee.com/kevin_chou</p>
				</view>
			</view>
		</view>

		<view style="height: 110rpx;width: 1rpx;"></view>

	</view>
</template>

<script>
	var videoAd = null
	export default {
		data() {
			return {
				// Custom: this.Custom,
				// CustomBar: this.CustomBar,
				spaceShow:true,
				modalName: null,
				picName: '流星之夜',
				pic: [{
					link: 'https://cdn.zhoukaiwen.com/zjx_me_bg1.jpeg',
					name: '春天'
				}, {
					link: 'https://cdn.zhoukaiwen.com/zjx_me_bg2.jpeg',
					name: '夏天'
				}, {
					link: 'https://cdn.zhoukaiwen.com/zjx_me_bg3.jpeg',
					name: '秋天'
				}, {
					link: 'https://cdn.zhoukaiwen.com/zjx_me_bg4.jpeg',
					name: '冬天'
				}, {
					link: 'https://cdn.zhoukaiwen.com/zjx_me_bg5.jpeg',
					name: '幽静'
				}, {
					link: 'https://cdn.zhoukaiwen.com/zjx_me_bg6.jpg',
					name: '天空'
				}],
				topBackGroupImageIndex: 5,
				inter: [{
					title: 'mimicry',
					name: '活力春天',
					color: ''
				}, {
					title: 'theme',
					name: '清爽夏日',
					color: ''
				}, {
					title: 'theme',
					name: '金秋之韵',
					color: ''
				}, {
					title: 'theme',
					name: '冬日之阳',
					color: ''
				}, {
					title: 'theme',
					name: '幽兰星空',
					color: ''
				}, {
					title: 'theme',
					name: '流星之夜',
					color: ''
				}]
			}
		},
		// 分享小程序
		onShareAppMessage(res) {
			return {
				title: '看看这个小程序多好玩～',
			};
		},
		watch:{
			topBackGroupImageIndex(val) {
				console.log(val)
				if (val == 4 || val == 5 ) {
					this.spaceShow = true;
				}else{
					this.spaceShow = false;
				}
			}
		},
		methods: {
			playVideo(){
				videoAd.show()
				.catch(() => {
				    videoAd.load()
				    .then(() => videoAd.show())
				    .catch(err => {
				      console.log('激励视频 广告显示失败')
				    })
				})
			},
			getGitee(){
				uni.setClipboardData({
				    data: 'https://gitee.com/kevin_chou',
				    success: function () {
				        console.log('success');
				    }
				});
			},
			switchImage(index, name) {
				this.topBackGroupImageIndex = index;
				this.modalName = null;
				this.picName = name;
			},
			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			showGitee(e){
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},

			// 答题测试
			mentalTest() {
				uni.navigateTo({
					url: '../me/mentalTest/list'
				})
			},
			//拨打固定电话
			callPhoneNumber() {
				uni.makePhoneCall({
					phoneNumber: "18629591093",
				});
			},
			goMedal(){
				uni.navigateTo({
					url: '../../tn_components/medal'
				})
			},
			// 关于作者
			goAboutMe() {
				uni.navigateTo({
					url: '../me/aboutMe'
				})
			},
			// 薪资排名
			// goSalary() {
			// 	uni.navigateTo({
			// 		url: '../me/salary'
			// 	})
			// },
			// // 课班信息
			// goCourse() {
			// 	uni.navigateTo({
			// 		url: '../me/course'
			// 	})
			// }
		}
	}
</script>

<style lang="scss" scoped>
	.UCenter-bg {
		background: #fff;
		background-size: 100% 100%;
		/* background-size: cover; */
		height: 550rpx;
		display: flex;
		justify-content: center;
		padding-top: 40rpx;
		overflow: hidden;
		position: relative;
		flex-direction: column;
		align-items: center;
		color: #fff;
		font-weight: 300;
		text-shadow: 0 0 3px rgba(0, 0, 0, 0.3);
	}

	.UCenter-bg text {
		opacity: 0.8;
	}

	.UCenter-bg image {
		width: 200rpx;
		height: 200rpx;
	}

	.UCenter-bg .gif-wave {
		position: absolute;
		width: 100%;
		bottom: 0;
		left: 0;
		z-index: 99;
		mix-blend-mode: screen;
		height: 100rpx;
	}


	// 头像
	.cu-avatar2 {
		font-variant: small-caps;
		margin: 0;
		padding: 0;
		display: inline-flex;
		text-align: center;
		justify-content: center;
		align-items: center;
		background: #ccc;
		color: #fff;
		white-space: nowrap;
		position: relative;
		width: 150rpx;
		height: 150rpx;
		background-size: cover;
		background-position: center;
		vertical-align: middle;
		font-size: 1.5em;
		z-index: 99;
	}

	.name {
		text-shadow: 2px 2px 1px #2f9bfe;
	}

	.dialog2 {
		background: none;
	}

	.saicode {
		background-size: 100% 100%;
		-moz-background-size: 100% 100%;
	}

	.img-big image {
		top: -40px;
		width: 280rpx;
		height: 280rpx;
	}


	.shadow-me {
		box-shadow: 0rpx 0rpx 100rpx 0rpx rgba(0, 0, 0, 0.1);
	}

	.tn-footerfixed {
		position: fixed;
		width: 100%;
		bottom: 0;
		z-index: 1024;
		box-shadow: 0 1rpx 6rpx rgba(0, 0, 0, 0.35);
	}

	.my_logo {
		background: none;
		padding: 50rpx 0 30rpx 0;
	}

	.my-radius {
		border-radius: 12rpx;
		overflow: hidden
	}

	.my-icon image {
		width: 100rpx;
		height: 100rpx;
		display: inline-block;
		margin: 0 auto
	}

	.my-iconcolor {
		background: rgba(255, 255, 255, 0.96)
	}

	.shadow-shop {
		box-shadow: 0rpx 0rpx 90rpx 0rpx rgba(0, 0, 0, 0.1);
	}

	.qrcode-img {
		position: fixed;
		width: 80rpx;
		height: 80rpx;
		bottom: 350rpx;
		right: 30rpx;
		z-index: 1024;
		opacity: 0.8;
		box-shadow: 0rpx 8rpx 30rpx 0rpx rgba(0, 0, 0, 0.3);
		border: none
	}


	/* 数字背景 */
	.shadow-warp-my {
		position: relative;
		box-shadow: 0 10rpx 10rpx rgba(0, 0, 0, 0.1);
	}

	.shadow-warp-my:before,
	.shadow-warp-my:after {
		position: absolute;
		content: "";
		top: 20rpx;
		bottom: 30rpx;
		left: 20rpx;
		width: 50%;
		box-shadow: 0 30rpx 20rpx rgba(0, 0, 0, 0.16);
		transform: rotate(-6deg);
		z-index: -1;
	}

	.shadow-warp-my:after {
		right: 20rpx;
		left: auto;
		transform: rotate(6deg);
	}


	.bg-product {
		background-image: linear-gradient(rgba(0, 0, 0, 0.06), rgba(0, 0, 0, 0));
		color: #fff;
	}

	.margin-bottom-my {
		margin-bottom: 150rpx;
	}
	.giteeClass{
		margin-top: 30rpx;
		font-size: 34rpx;
		color: #2440B3;
		text-decoration: underline;
	}
	.cu-dialog {
		background: #FFFFFF;
		overflow: visible;
	}

	.modal_bg {
		width: 100%;
		height: 400rpx;
		position: absolute;
		top: -100rpx;
		background-image: url(https://zhoukaiwen.com/img/qdpz/modal_bg.png);
		background-size: 100%;
		background-repeat: no-repeat;
	}

	.modal_main {
		background-color: #FFFFFF;
	}

	/* 主题色 */
	.bg-zt1 {
		color: #fff;
		background: #81d949;
	}

	.bg-zt2 {
		color: #fff;
		background: #b2e6ff;
	}

	.bg-zt3 {
		color: #fff;
		background: #f3cd41;
	}

	.bg-zt4 {
		color: #fff;
		background: #ddecf7;
	}

	.bg-zt5 {
		color: #fff;
		background: #152e9d;
	}
	
	.bg-zt6 {
		color: #fff;
		background: #0f1358;
	}

	.nav-list {
		display: flex;
		flex-wrap: wrap;
		padding: 0px 40upx 0px;
		justify-content: space-between;
	}

	.nav-li {
		padding: 22upx;
		border-radius: 12upx;
		width: 45%;
		margin: 0 2.5% 40upx;
		background-image: url(/static/home.png);
		background-size: cover;
		background-position: center;
		position: relative;
		z-index: 1;
	}

	.nav-li::after {
		content: "";
		position: absolute;
		z-index: -1;
		background-color: inherit;
		width: 100%;
		height: 100%;
		left: 0;
		bottom: -10%;
		border-radius: 10upx;
		opacity: 0.2;
		transform: scale(0.9, 0.9);
	}

	.nav-li.cur {
		color: #fff;
		background: rgb(94, 185, 94);
		box-shadow: 4upx 4upx 6upx rgba(94, 185, 94, 0.4);
	}

	.nav-name {
		font-size: 28upx;
		text-transform: Capitalize;
		position: relative;
	}

	.nav-name::before {
		content: "";
		position: absolute;
		display: block;
		width: 40upx;
		height: 6upx;
		background: #fff;
		bottom: 0;
		right: 0;
		opacity: 0.5;
	}

	.nav-name::after {
		content: "";
		position: absolute;
		display: block;
		width: 100upx;
		height: 1px;
		background: #fff;
		bottom: 0;
		right: 40upx;
		opacity: 0.3;
	}

	.nav-name::first-letter {
		font-weight: bold;
		font-size: 36upx;
		margin-right: 1px;
	}

	.nav-li text {
		position: absolute;
		right: 30upx;
		top: 30upx;
		font-size: 52upx;
		width: 60upx;
		height: 60upx;
		text-align: center;
		line-height: 60upx;
	}

</style>
