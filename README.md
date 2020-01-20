# 壹本印画小程序

## Project setup 安装依赖
```
npm install || cnpm i

```

## 开发环境启动
## HbuilderX 工具 运行(R) -> 运行到小程序模拟器(M)

// 订单列表按钮 我要加印
将订单卡片内的所有订单项加入购物车并跳转购物车，每个订单项构成一张卡片并自动勾选上计算价格
 

// 订单列表按钮 继续支付
直接调起支付


// 订单列表按钮 确认收货
跳转到订单详情页 状态传值 已完成




------------------------------------------------------------ 接口部分 --------------------------------------------------------
1. 购物车
    /mobile/cart/getOrderList		查询购物车卡片数据
    参数
    {
        openId: ‘12149212148’  用户微信openid
    }
    响应数据
    {
        // 卡片数据
        orderList:[
            {
                isgroupon: false,
                bookName: '无感',
                bookType: '32开标准本',
                editType: '自编辑',
                pageCount: '96P',
                bookSize: '144*192mm',
                price: '98.00',
                tips:['*第一本98元，同一内容加印价88元'],
                quantity: 1,                // 写死 
                isSelect: false             // 写死
            },
            {
                isgroupon: true,
                bookName: '满足',
                bookType: '32开标准本',
                editType: '设计师',
                pageCount: '96P',
                bookSize: '144*192mm',
                price: '98.00',
                tips:[
                    '*该活动产品不与其他优惠同享，仅限现金支付',
                    '非活动产品如需使用现金码/壹本币支付，清分开结算'
                ],
                quantity: 1,                // 写死
                isSelect: false             // 写死
            }
        ],
        
    }


2. 个人中心
    /mobile/personal/getUserInfo         获取用户openid
    参数
    {
        code: 'HGWAOHIGIAWOIGOH'      uni.login登陆参数
    }
    响应数据
    {
        openId : 'afgwhalgiwahil'
    }


    /mobile/personal/walletOpen          开通一本钱包
    参数
    {
        后台定
    }
    响应数据
    {
        isOpen : true
    }


3. 团购列表
    /mobile/groupon/getNavList   // 页面加载获取导航栏模块列表
    参数
    {}
    响应数据
    {
        tabTitle:['照片书','热门活动']
    }

    /mobile/groupon/getCardList     // 获取所有导航栏模块卡片数据
    参数
    {}
    响应数据
    {
        getCardList: [
            // tabTitle 导航栏第一个模块页面卡片数据, 
            [
                        {
							grouponCardId: '01',					// 每个模块的每个卡片拥有唯一键(跳转详情页作为请求参数)
                            imgSrc: '',
                            activeName: '莫兰迪油白系列',
                            ad: '大师同款，限时特惠！售完即止，手慢无!',
                            originalPrice: [308,388],               // 原价(范围)
                            stock: 20,
                            activeStartTime: '1568465156',
                            activeEndTime: '189456156',
                            price: [240,308],                       // 活动价(范围)
                        },
                        {
							grouponCardId: '02',						// 每个模块的每个卡片拥有唯一键
                            imgSrc: '',
                            activeName: '精装布面小开本',
                            ad: '大师同款，限时特惠！售完即止，手慢无!',
                            originalPrice: [308,388],               // 原价(范围)
                            stock: 88,
                            activeStartTime: '1568465156',
                            activeEndTime: '189456156',
                            price: [240,308],                       // 活动价(范围,无范围数组一个元素就好)
                        }
            ],
            // tabTitle 导航栏第二个模块页面卡片数据，依次类推
            [
						{
							grouponCardId: '03',						// 每个模块的每个卡片拥有唯一键
						    imgSrc: '',
						    activeName: '热门活动产品',
						    ad: '大师同款，限时特惠！售完即止，手慢无!',
						    originalPrice: [308,388],               // 原价(范围)
						    stock: 88,
						    activeStartTime: '1568465156',
						    activeEndTime: '189456156',
						    price: [240,308],                       // 活动价(范围,无范围数组一个元素就好)
						}
			]                    
        ]
    }


4. 团购详情     (未完待续...)
    /mobile/groupon/getDetailsInfo          // 获取团购列表卡片对应详情数据
    参数
    {
        grouponCardId: ''    (string)
    }
    响应数据
    {
        detailsInfo: {
            bannerImgList: ['','',''],					// banner 图片路径
			soldNum: 33,								// 已售件数
			productDetailsImgList: ['','','','','','']	// 产品详情图片路径			
		}
    }


5. 我的书架     (待完善)
    /mobile/bookshelf/getBoardInfo            // 获取用户最近编辑的作品名
    参数
    {}
    响应数据
    boardInfo: {
		bookName: '哈哈哈哈哈'
	},





    /mobile/bookshelf/getWorksList            // 获取我的书架卡片数据(无则返回空对象)
    参数
    {}
    响应数据
    {
        worksList: [
                    {
                        imgSrc: '',						// 作品封面图
                        bookName: '再见杰克',
                        bookType: '精装布面本小开本',
                        bookSpec: '192P',
						editType: '自编辑',
						status: 0						// 作品卡片状态 0: 编辑中  1: 已完成
                    },
                    {
                        imgSrc: '',
                        bookName: '他夏了夏天',
                        bookType: '精装布面本小开本',
                        bookSpec: '192P',
						editType: '设计师',
						status: 1
                    },
					
        ]
    }



6. 我的钱包     (待完善)
    /mobile/wallet/getWalletInfo           // 获取用户余额
    参数
    {
        openId: 'gaghlawigl2ih3li',          // 用户数据表主键openId?
    }
    响应数据
    {
        balance: '180.00',
        isOpen: ture                        // 用户是否开通钱包标识   false  true   
    }


    /mobile/wallet/quotaOptionsList           // 获取充值额度选项数据
    参数
    {}
    响应数据
    {
        quotaOptionsList: [
					{
						quotaText: '200',	// 壹本币额度
						quotaGive: '20',	// 充值送 
						quota: '200.00',	// 实际应付金额
						isDouble: '0',		// 是否具有首充双倍优惠活动		0: 无  1: 有
						isRecommend: '0',	// 是否推荐			0: 不推荐	1: 推荐
						select: '0',		// 写死
					},
					{
						quotaText: '500',	// 壹本币额度
						quotaGive: '100',	// 充值送 
						quota: '500.00',	// 实际应付金额
						isDouble: '0',		// 是否具有首充双倍优惠活动		0: 无  1: 有
						isRecommend: '0',	// 是否推荐			0: 不推荐	1: 推荐
						select: '0',		// 写死
					},
					{
						quotaText: '1000',	// 壹本币额度
						quotaGive: '250',	// 充值送 
						quota: '250.00',	// 实际应付金额
						isDouble: '1',		// 是否具有首充双倍优惠活动		0: 无  1: 有
						isRecommend: '1',	// 是否推荐			0: 不推荐	1: 推荐
						select: '0',		// 写死
					},
					{
						quotaText: '3000',	// 壹本币额度
						quotaGive: '1000',	// 充值送 
						quota: '1000.00',	// 实际应付金额
						isDouble: '1',		// 是否具有首充双倍优惠活动		0: 无  1: 有
						isRecommend: '1',	// 是否推荐			0: 不推荐	1: 推荐
						select: '0',		// 写死
					},
		]
    }



7. 账单明细
    /mobile/wallet/getCardList           // 获取充值账单&交易明细卡片列表数据
    参数
    {
        flag: '0'               // 0: 获取充值账单卡片列表      1: 获取交易明细卡片列表
    }
    响应数据
    {
        billCardList: [
					// 筛选(全部)
					[
						{
							orderStatus: '0',						// 账单卡片状态 '0': 待付款	'1': 已完成	
							orderId: '213',							// 订单编号
							desc: '【优惠活动】买1000送250',			// 账单卡片描述
							totalPrice: '1000.00',					// 合计价格
							orderCreatTime: '2020-01-13 12:50:48',	// 订单创建时间
						},
						{
							orderStatus: '1',						// 账单卡片状态 '0': 待付款	'1': 已完成	
							orderId: '214',							// 订单编号
							desc: '【优惠活动】买1000送250',			// 账单卡片描述
							totalPrice: '2000.00',					// 合计价格
							orderCreatTime: '2020-01-15 12:50:48',	// 订单创建时间	
						},
						{
							orderStatus: '1',						// 账单卡片状态 '0': 待付款	'1': 已完成	
							orderId: '215',							// 订单编号
							desc: '【优惠活动】买1000送250',			// 账单卡片描述
							totalPrice: '5000.00',					// 合计价格
							orderCreatTime: '2020-01-14 12:50:48',	// 订单创建时间
						},
					],
					// 筛选(待付款)
					[
						{
							orderStatus: '0',						// 账单卡片状态 '0': 待付款	'1': 已完成	
							orderId: '213',							// 订单编号
							desc: '【优惠活动】买1000送250',			// 账单卡片描述
							totalPrice: '1000.00',					// 合计价格
							orderCreatTime: '2020-01-13 12:50:48',	// 订单创建时间
						},
					],
					// 筛选(已完成)
					[
						{
							orderStatus: '1',						// 账单卡片状态 '0': 待付款	'1': 已完成	
							orderId: '214',							// 订单编号
							desc: '【优惠活动】买1000送250',			// 账单卡片描述
							totalPrice: '2000.00',					// 合计价格
							orderCreatTime: '2020-01-15 12:50:48',	// 订单创建时间	
						},
						{
							orderStatus: '1',						// 账单卡片状态 '0': 待付款	'1': 已完成	
							orderId: '215',							// 订单编号
							desc: '【优惠活动】买1000送250',			// 账单卡片描述
							totalPrice: '5000.00',					// 合计价格
							orderCreatTime: '2020-01-14 12:50:48',	// 订单创建时间
						},
					]
	
				],
    }

    参数
    {
        flag: '1'               // 0: 获取充值账单卡片列表      1: 获取交易明细卡片列表
    }
    响应数据
    {
        detailsCardList: [
					// 筛选 (全部)
					[
						{
							Budget: '0',							// 收入/支出 1/0
							dec: '【优惠活动】买1000送250',			// 交易描述
							price: '1000.00',						// 交易金额(收入或支出)
							businessTime: '2020-01-13 12:50:48',	// 交易时间
						},
						{
							Budget: '1',							// 收入/支出 1/0
							dec: '【优惠活动】买1000送250',			// 交易描述
							price: '3000.00',						// 交易金额(收入或支出)
							businessTime: '2020-01-15 12:50:48',	// 交易时间
						},
						{
							Budget: '1',							// 收入/支出 1/0
							dec: '【优惠活动】买1000送250',			// 交易描述
							price: '2000.00',						// 交易金额(收入或支出)
							businessTime: '2020-01-14 12:50:48',	// 交易时间
						}
					],
					// 筛选 (收入)
					[
						{
							Budget: '1',							// 收入/支出 1/0
							dec: '【优惠活动】买1000送250',			// 交易描述
							price: '3000.00',						// 交易金额(收入或支出)
							businessTime: '2020-01-15 12:50:48',	// 交易时间
						},
						{
							Budget: '1',							// 收入/支出 1/0
							dec: '【优惠活动】买1000送250',			// 交易描述
							price: '2000.00',						// 交易金额(收入或支出)
							businessTime: '2020-01-14 12:50:48',	// 交易时间
						}
					],
					// 筛选 (支出)
					[
						{
							Budget: '0',							// 收入/支出 1/0
							dec: '【优惠活动】买1000送250',			// 交易描述
							price: '1000.00',						// 交易金额(收入或支出)
							businessTime: '2020-01-13 12:50:48',	// 交易时间
						},
					],
					
				]
    }












