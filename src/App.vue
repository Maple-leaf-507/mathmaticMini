<script setup lang="ts">
import { onLaunch, onShow, onHide } from "@dcloudio/uni-app";
onLaunch(() => {
	const updateManager = uni.getUpdateManager();
	
	updateManager.onCheckForUpdate(function (res) {
		if (res.hasUpdate) {
			updateManager.onUpdateReady(function (res) {
				uni.showModal({
					title: '更新提示',
					content: '新版本已经准备好，是否重启应用？',
					success(res) {
						if (res.confirm) {
							// 新的版本已经下载好，调用 applyUpdate 应用新版本并重启
							updateManager.applyUpdate();
						}
					}
				});
			});

			// 小程序有新版本，会主动触发下载操作（无需开发者触发）
			updateManager.onUpdateFailed(async () => {
				// 当新版本下载失败，会进行回调
				uni.showModal({
					title: '提示',
					content: '检查到有新版本，但下载失败，请稍后尝试'
				});
			})
		}
	});
});
onShow(() => {
//   console.log("App Show");
});
onHide(() => {
//   console.log("App Hide");
});
</script>
<style>

</style>
