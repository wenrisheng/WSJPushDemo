<template>
	<view class="content">
		<view class="">
			-----V1.7.6 更新时间：08.24-----
		</view>
		<button type="default" @click="setMobileNumber()">
			设置手机号
		</button>
		<view class="">
			-----V1.7.5 更新时间：08.07-----
		</view>
		<button type="default" @click="ios_addLocalNotification()">
			iOS本地推送
		</button>
		<view class="">
			-----V1.7.0 更新时间：07.15-----
		</view>
		<button type="default" @click="ios_setMsgNotiType()">
			iOS设置消息通知方式（前台）
		</button>
		<view class="">
			-----V1.6.0 更新时间：04.27-----
		</view>
		<button type="default" @click="jy_setTags()">
			以数组方式设置Tags
		</button>

		<view class="">
			-----V1.5.0 更新时间：01.06-----
		</view>
		<view class="" @click="ios_requestNotificationAuthorization()">
			ios请求通知权限
		</view>
		<view class="" @click="ios_openSettingsForNotification()">
			ios打开通知设置
		</view>
		<view class="" @click="android_isNotificationEnabled()">
			android判断是否打开通知
		</view>
		<view class="" @click="android_goToAppNotificationSettings()">
			android打开通知设置
		</view>
		<view class="" @click="android_setBadgeNumber()">
			android设置角标（暂时只支持华为）
		</view>

		<view class="">
			-----以前的API-----
		</view>
		<view class="" @click="getRegisterID()">
			获取RegisterID
		</view>

		<view class="" @click="setupJYJPush()">
			设置Alias
		</view>
		<view class="" @click="deleteJYJPushAlias()">
			删除Alias
		</view>

		<view class="" @click="addJYJPushReceiveNotificationListener()">
			监听推送
		</view>
		<view class="" @click="addJYJPushReceiveOpenNotificationListener()">
			监听推送打开（后台）
		</view>
		<view class="" @click="getAPPKeyClick()">
			获取APPKEY
		</view>

		<view class="" @click="getLastPushInfo()">
			获取最后的推送数据
		</view>

		<view class="">
			-----V1.3.0 更新时间：10.08-----
		</view>
		<view class="" @click="addJYJPushTags()">
			新增Tags
		</view>
		<view class="" @click="setJYJPushTags()">
			设置Tags
		</view>
		<view class="" @click="deleteJYJPushTags()">
			删除某一个Tags
		</view>
		<view class="" @click="cleanJYJPushTags()">
			清空所有的tags
		</view>
		<view class="" @click="getJYJPushTags()">
			查询已经设置的tags
		</view>
		<view class="" @click="validJYJPushTags()">
			验证某个tag是否已经设置
		</view>

		<view class="">
			------V1.3.0以下方法仅iOS支持------
		</view>
		<view class="" @click="setJYJPushBadge()">
			设置角标
		</view>
		<view class="" @click="resetJYJPushBadge()">
			清空角标
		</view>
		<view class="">
			------V1.3.0以下方法仅安卓支持------
		</view>
		<view class="" @click="stopJYJPush()">
			停止接收推送
		</view>
		<view class="" @click="resumeJYJPush()">
			继续接收推送
		</view>
		<view class="">
			-----V1.4.0 更新时间：10.17-----
		</view>
		<view class="" @click="addJYJPushCustomReceiveNotificationListener()">
			监听自定义消息的推送
		</view>
		<view class="">
			-----V1.4.5 更新时间：11.18-----
		</view>
		<view class="" @click="addJYJPushReceiveBackgroudNotificationListener()">
			监听后台消息的推送（进程未被杀死）
		</view>
		<view class="">
			-----V1.4.6 更新时间：12.02----- 本次方法仅支持安卓
		</view>
		<view class="" @click="android_addLocalNotification()">
			添加本地推送（安卓）
		</view>
		<view class="" @click="android_removeLocalNotification()">
			清除本地推送（安卓）
		</view>
		<view class="" @click="android_clearLocalNotifications()">
			清空本地推送（安卓）
		</view>



		<view class="">
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			setMobileNumber() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.setMobileNumber({
					mobileNumber: "13281055555"
				}, res=> {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(res)
					})
					console.log(JSON.stringify(res));
				})
			},
			ios_addLocalNotification() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.ios_addLocalNotification({
					builderId: '102',
					content: "推送的内容",
					title: "推送的Title",
					notificationId: "1",
					year: "2019", // 预约发送的时间，若小于当前时间，则立即发送；若大于当前时间，则预约时间，时间到了就发送；但是APP需要在前台
					month: "12",
					day: "02",
					hour: "21",
					minute: "20",
					second: "21",
					extra: {
						"a": "1",
						"b": "2"
					}
				}, res => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(res)
					})
					console.log(JSON.stringify(res));
				})
			},
			ios_setMsgNotiType() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.ios_setMsgNotiType({
					type: '102'
				}, res => {

				})
			},
			//	V1.6.1
			jy_setTags() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.addJYJPushTagsWithArr({
					userTags: [
						"1",
						"2",
						"3"
					]
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
					console.log(JSON.stringify(result));
				});
			},
			// V1.5.0
			android_setBadgeNumber() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.android_setBadgeNumber({
					badgeNumber: "1"
				}, result => {
					console.log(JSON.stringify(result));
				});
			},
			android_goToAppNotificationSettings() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.android_goToAppNotificationSettings(result => {
					console.log(JSON.stringify(result));
				});
			},
			android_isNotificationEnabled() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.android_isNotificationEnabled(result => {
					console.log(JSON.stringify(result));
				});
			},
			ios_openSettingsForNotification() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.ios_openSettingsForNotification(result => {
					console.log(JSON.stringify(result));
				});
			},
			ios_requestNotificationAuthorization() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.ios_requestNotificationAuthorization(result => {
					console.log(JSON.stringify(result));
				});
			},

			//	V1.4.6
			android_addLocalNotification() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.android_addLocalNotification({
					builderId: "1", // builderId 编号，自己定义，如果不管，可以全部传递1
					content: "推送内容",
					title: "推送标题",
					notificationId: "1", // 消息ID，需要为数字，后续可以通过这个取消,
					year: "2019", // 预约发送的时间，若小于当前时间，则立即发送；若大于当前时间，则预约时间，时间到了就发送；但是APP需要在前台
					month: "12",
					day: "02",
					hour: "21",
					minute: "20",
					second: "21"
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			android_removeLocalNotification() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.android_removeLocalNotification({
					notificationId: "1", // 消息ID，需要为数字
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			android_clearLocalNotifications() {

				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.android_clearLocalNotifications(result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			//	V1.4.5
			addJYJPushReceiveBackgroudNotificationListener() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.addJYJPushReceiveBackgroudNotificationListener(result => {
					uni.showToast({
						icon: 'none',
						title: 'recback' + JSON.stringify(result)
					})
					console.log(JSON.stringify(result));
				});

			},

			//	V1.4.0 新增
			addJYJPushCustomReceiveNotificationListener() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.addJYJPushCustomReceiveNotificationListener(result => {
					uni.showToast({
						icon: 'none',
						title: 'ReceiveCustomNotificationListener' + JSON.stringify(result),
					})


				});
			},

			//	V1.3.0 新增方法
			resumeJYJPush() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.resumeJYJPush(result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			stopJYJPush() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.stopJYJPush(result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			resetJYJPushBadge() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.resetJYJPushBadge(result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			setJYJPushBadge() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.setJYJPushBadge({
					value: '0-9999之间'
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			validJYJPushTags() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.validJYJPushTags({
					userTag: '需要验证的tag'
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			getJYJPushTags() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.getJYJPushTags(
					result => {
						uni.showToast({
							icon: 'none',
							title: JSON.stringify(result)
						})
					});
			},
			cleanJYJPushTags() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.cleanJYJPushTags(
					result => {
						uni.showToast({
							icon: 'none',
							title: JSON.stringify(result)
						})
					});
			},
			deleteJYJPushTags() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.deleteJYJPushTags({
					userTag: '删除某一个tag'
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			setJYJPushTags() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.setJYJPushTags({
					userTag: '设置自己想要的tag'
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			addJYJPushTags() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.addJYJPushTags({
					userTag: '新增自己想要的tag'
				}, result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			getLastPushInfo() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.getLastPushInfo(result => {
					console.log(JSON.stringify(result));
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			getAPPKeyClick() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.getAPPKey(result => {
					console.log(JSON.stringify(result));
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			addJYJPushReceiveOpenNotificationListener() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.addJYJPushReceiveOpenNotificationListener(result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			addJYJPushReceiveNotificationListener() {
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.addJYJPushReceiveNotificationListener(result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			getRegisterID() {
				console.log('获取RegisterID');
				const jyJPush = uni.requireNativePlugin('JY-JPush');
				jyJPush.getRegistrationID(result => {
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			},
			setupJYJPush() {
				console.log('setupJYJPush');
				const jyJPush = uni.requireNativePlugin('JY-JPush');

				jyJPush.setJYJPushAlias({
					userAlias: 'testAlias22'
				}, result => {
					console.log(JSON.stringify(result));
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});

			},
			deleteJYJPushAlias() {
				console.log('deleteJYJPushAlias');
				const jyJPush = uni.requireNativePlugin('JY-JPush');

				jyJPush.deleteJYJPushAlias({

				}, result => {
					console.log(JSON.stringify(result));
					uni.showToast({
						icon: 'none',
						title: JSON.stringify(result)
					})
				});
			}

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50upx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
