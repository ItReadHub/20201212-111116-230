# 抖音协议、抖音接口批量评论技术探讨

<a name="JvJWk"></a>
### 1、抓包获取评论API
```
POST /aweme/v1/comment/publish/?manifest_version_code=750&_rticket=1585579972079&app_type=normal&iid=109603465232&channel=wandoujia_aweme2&device_type=HWI-AL00&language=zh&uuid=868793039197273&resolution=1080*2160&openudid=9ba4839bf09a1834&update_version_code=7502&os_api=28&dpi=480&ac=wifi&device_id=50745463573&mcc_mnc=46001&os_version=9&version_code=750&app_name=aweme&version_name=7.5.0&js_sdk_version=1.19.4.16&device_brand=HUAWEI&ssmix=a&device_platform=android&aid=1128&ts=1585579971 HTTP/1.1
 
 
body:aweme_id=6809397725809872141&text=你好&text_extra=%5B%5D&is_self_see=0&channel_id=0
```
<a name="OnNd1"></a>
### 2、X-GORGON获取
通过参数进行组装排序请求加密函数，得到X-GORGON
<a name="3N47m"></a>
### 3、上代码
随便写了个演示的，将就着看吧：
```python
import requests
import time
#评论
for line in open("vids.txt","r",encoding='UTF-8'):
    print(line)
    host = 'http://host'
    sid_guard = 'xxx'
    proxyip = 'xxx'
    para = {
        "manifest_version_code": "750",
        "app_type": "normal",
        "iid": "xx",
        "channel": "wandoujia_aweme2",
        "device_type": "HWI-AL00",
        "language": "zh",
        "uuid": "xx",
        "resolution": "1080*2160",
        "openudid": "xx",
        "update_version_code": "7502",
        "os_api": "28",
        "dpi": "480",
        "ac": "wifi",
        "device_id": "xx",
        "mcc_mnc": "46001",
        "os_version": "9",
        "version_code": "750",
        "app_name": "aweme",
        "version_name": "7.5.0",
        "js_sdk_version": "1.19.4.16",
        "device_brand": "HUAWEI",
        "ssmix": "a",
        "device_platform": "android",
        "aid": "1128"
    }
    commentUrl = host+'/operate/video/comment?token=xxx&aweme_id=xxx&txt='+line.split("-")[1]+'&sid_guard=xxx&proxyip=xxx
    cResp = requests.post(commentUrl,data=para)
    print(cResp.text)
```

<br />执行结果如下：
```python
{
	"code": 200,
	"data": {
		"status_code": 0,
		"status_msg": "评论成功",
		"comment": {
			"digg_count": 0,
			"status": 7,
			"user_digged": 0,
			"reply_comment": [],
			"text_extra": [],
			"reply_to_reply_id": "0",
			"text": "\
			u4f60\ u597d\ u554a ",
			"
			aweme_id ": "
			6772424922141560077 ", "
			create_time ": 1585579023, "
			user ": {"
			weibo_name ": "
			", "
			weibo_schema ": "
			", "
			account_region ": "
			", "
			is_discipline_member ": false, "
			follower_status ": 0, "
			gender ": 0,
			"signature": "",
			"favoriting_count": 0,
			"hide_location": false,
			"unique_id_modify_time": 1585579023,
			"uid": "96702335529",
			"user_mode": 0,
			"has_unread_story": false,
			"has_facebook_token": false,
			"followers_detail": n
			ull,
			"commerce_user_level": 0,
			"ins_id": "",
			"follow_status": 0,
			"is_block": false,
			"authority_status": 0,
			"relative_users": null,
			"weibo_url": "",
			"has_twitter_token": false,
			"youtube_channel_title": "",
			"user_cancel
			ed ": false, "
			download_prompt_ts ": 0, "
			follower_count ": 0, "
			has_email ": false, "
			region ": "
			CN ", "
			prevent_download ": false, "
			youtube_channel_id ": "
			", "
			item_list ": null, "
			cv_level ": "
			", "
			type_label ": null, "
			school_name ":
			"",
			"show_image_bubble": false,
			"user_rate": 1,
			"cover_url": [{
						"uri": "c8510002be9a3a61aad2",
						"url_list": ["https://p9-dy.byteimg.com/obj/c8510002be9a3a61aad2?from=2956013662", "https://p1-dy.byteimg.com/obj/c8510002b
								e9a3a61aad2 ? from = 2956013662 ", "
								https : //p3-dy.byteimg.com/obj/c8510002be9a3a61aad2?from=2956013662"], "width": 720, "height": 720}], "ad_cover_url": null, "comment_filter_status": 0, "need_points": null, "total_favorit
								ed ": 0, "
								story_count ": 0, "
								youtube_expire_time ": 0, "
								new_story_cover ": null, "
								location ": "
								", "
								need_recommend ": 1, "
								story_open ": false, "
								sync_to_toutiao ": 0, "
								user_period ": 0, "
								avatar_168x168 ": {"
								width ": 720, "
								height ":
								720, "uri": "93e0001f51ea84265261", "url_list": ["http://p9-dy.byteimg.com/img/mosaic-legacy/93e0001f51ea84265261~168x168.webp", "http://p29-dy.byteimg.com/img/mosaic-legacy/93e0001f51ea84265261~168x168.webp", "http:
									//p3-dy.byteimg.com/img/mosaic-legacy/93e0001f51ea84265261~168x168.webp"]}, "enterprise_verify_reason": "", "neiguang_shield": 0, "avatar_thumb": {"uri": "93e0001f51ea84265261", "url_list": ["https://p9-dy.byteimg.com
									/
									aweme / 100 x100 / 93e0001 f51ea84265261.jpeg ", "
									https: //p29-dy.byteimg.com/aweme/100x100/93e0001f51ea84265261.jpeg", "https://p3-dy.byteimg.com/aweme/100x100/93e0001f51ea84265261.jpeg"], "width": 720, "height": 720}, "ava
									tar_medium ": {"
									uri ": "
									93e0001 f51ea84265261 ", "
									url_list ": ["
									https: //p9-dy.byteimg.com/aweme/720x720/93e0001f51ea84265261.jpeg", "https://p29-dy.byteimg.com/aweme/720x720/93e0001f51ea84265261.jpeg", "https://p3-dy.bytei
									mg.com / aweme / 720 x720 / 93e0001 f51ea84265261.jpeg "], "
									width ": 720, "
									height ": 720}, "
									constellation ": 0, "
									live_verify ": 0, "
									live_agreement ": 0, "
									accept_private_policy ": false, "
									reflow_page_uid ": 0, "
									shield_comment_notice ":
									0, "school_poi_id": "", "with_fusion_shop_entry": false, "sec_uid": "MS4wLjABAAAAsGYK_lUuj6y-arWdaDF1JdapPABgXsYHrTnbLlzrKYU", "avatar_larger": {
										"uri": "93e0001f51ea84265261",
										"url_list": ["https://p9-dy.byteimg.com/
											aweme / 1080 x1080 / 93e0001 f51ea84265261.jpeg ", "
											https: //p29-dy.byteimg.com/aweme/1080x1080/93e0001f51ea84265261.jpeg", "https://p3-dy.byteimg.com/aweme/1080x1080/93e0001f51ea84265261.jpeg"], "width": 720, "height": 720},
											"special_lock": 1, "room_id": 0, "create_time": 1575456559, "comment_setting": 0, "is_ad_fake": false, "react_setting": 0, "fb_expire_time": 0, "google_account": "", "live_commerce": false, "language": "zh-Hans", "is
											_star ": false, "
											unique_id ": "
											dyn4o0eeycmd ", "
											tw_expire_time ": 0, "
											reflow_page_gid ": 0, "
											cha_list ": null, "
											bind_phone ": "
											", "
											with_commerce_entry ": false, "
											video_icon ": {"
											uri ": "
											", "
											url_list ": [], "
											width ": 720, "
											height ": 720
										},
										"is_gov_media_vip": false,
										"geofencing": [],
										"is_verified": true,
										"hide_search": true,
										"weibo_verify": "",
										"custom_verify": "",
										"secret": 0,
										"with_dou_entry": false,
										"twitter_id": "",
										"nickname": "用户
										673433051 ", "
										platform_sync_info ": null, "
										following_count ": 0, "
										has_insights ": false, "
										birthday ": "
										", "
										is_binded_weibo ": false, "
										has_youtube_token ": false, "
										school_type ": 0, "
										with_shop_entry ": false, "
										has_orders ": fals
										e,
										"duet_setting": 0,
										"short_id": "2978172594",
										"twitter_name": "",
										"verify_info": "",
										"shield_digg_notice": 0,
										"download_setting": -1,
										"verification_type": 1,
										"avatar_uri": "93e0001f51ea84265261",
										"aweme_count": 0,
										"
										apple_account ": 0, "
										is_phone_binded ": false, "
										avatar_300x300 ": {"
										uri ": "
										93e0001 f51ea84265261 ", "
										url_list ": ["
										http: //p9-dy.byteimg.com/img/mosaic-legacy/93e0001f51ea84265261~300x300.webp", "http://p29-dy.byteimg.com/im
											g / mosaic - legacy / 93e0001 f51ea84265261~300 x300.webp ", "
										http: //p3-dy.byteimg.com/img/mosaic-legacy/93e0001f51ea84265261~300x300.webp"], "width": 720, "height": 720}, "homepage_bottom_toast": null, "shield_follow_notice":
											0,
										"live_agreement_time": 0,
										"status": 1
									}, "reply_id": "0", "cid": "6810010041757319179"
								}, "label_info": "", "extra": {
									"now": 1585579023000,
									"fatal_item_ids": [],
									"logid": "202003302237030101440621011327D83E"
								}, "log_
								pb ": {"
								impr_id ": "
								202003302237030101440621011327 D83E "}}, "
								success ": 1}
```
完美搞定，通过协议的方式可进行批量操作<br />
<br />——————————————————————————————————————————
<a name="9794cc28"></a>
#### TiToData：专业的短视频、直播数据接口服务平台。
<a name="1c5f89ff"></a>
#### 更多信息请联系： [TiToData](https://www.titodata.com?from=douyinarticle)
覆盖主流平台：抖音，快手，小红书，TikTok，YouTube
