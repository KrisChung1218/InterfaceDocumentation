# 壹本印画小程序


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
                dataIndex: '01'     // 卡片标识
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
                dataIndex: '02'     // 卡片标识
            }
        ],
        
    }

    /mobile/cart/delteCard		删除购物车卡片
    参数
    {
        dataIndex: dataIndex  // 卡片对应标识dataIndex
    }
    响应数据
    {
        200
    }

    /mobile/cart/settleAccounts		结算购物车  复用公众号接口  细节再做交流
    



2. 个人中心     (待完善)
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
    {}
    响应数据
    {
        200
    }

    /mobile/personal/checkBalance          查询钱包余额(用户每次进入个人中心都会调用查询)
    参数
    {}
    响应数据
    {
        balance: '180.00'       
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


4. 团购详情    
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

    /mobile/groupon/addToCart          // 用户点击加入购物车选定规格后  点击加入购物车调用addToCart接口
    参数
    {}
    响应数据
    {
        返回200
    }

    /mobile/groupon/buyNow          // 用户点击立即抢按钮选定规格后  点击立即抢调用buyNow接口跳转结算页面
    参数
    {}
    响应数据
    {
        返回200
    }



5. 我的书架     
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



    /mobile/bookshelf/getAllWorksOptionsList            // 获取下拉框分类数据
    参数
    {}
    响应数据
    {
        allWorksOptionsList: [
                    {
                        text: '全部产品'
                    },
                    {
                        text: '照片书'
                    },
                    {
                        text: '照片书'
                    },
                    {
                        text: '照片书'
                    },
                    {
                        text: '照片书'
                    },
                    {
                        text: '照片书'
                    },
                    {
                        text: '照片书'
                    },
                ],
    }



6. 我的钱包     (待完善)
    /mobile/wallet/getWalletInfo           // 获取用户余额
    参数
    {
        openId: 'gaghlawigl2ih3li',          // 用户数据表主键,是否为openId?
    }
    响应数据
    {
        balance: '180.00',
        isOpen: ture                        // 用户是否开通钱包标识   false  true || '0' '1'   
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

    /mobile/wallet/payNow           // 立即充值 
    参数
    {
        quota: quota  // 用户选项实付金额
    }
    响应数据
    {
        200
    }



7. 结算页面 
    /mobile/settlement/getUserReceiptInfoList          // 获取用户编辑的收件信息列表
    参数
    {
        openId: 'gagwagagwagawgga'                  
    }
    响应数据
    {
        userReceiptInfoList: [                      
                    {
                        userName: '豆豆',
                        phoneNumber: '15995520706',
                        fullAddress: '上海市徐汇区长桥街道平福路漕河泾聚鑫园188号3号楼3楼',
                        isSelect: '1'           // 写死
                    },
                    {
                        userName: 'alice',
                        phoneNumber: '15995520706',
                        fullAddress: '上海市徐汇区长桥街道平福路漕河泾聚鑫园188号3号楼3楼',
                        isSelect: '0'           // 写死
                    },
                    {
                        userName: 'bans',
                        phoneNumber: '18155925790',
                        fullAddress: '杭州市西湖区',
                        isSelect: '0'           // 写死
                    }
                ],
    }


    /mobile/settlement/getSettlementInfo            // 获取用户结算信息
    参数
    {
        orderId: '1001'                 // 购物车用户点击结算按钮请求接口创建订单orderId  传值到结算页
    }
    响应数据
    {
        cardSpecList: [
                        {
                            imgSrc: '',                 // 作品封面
                            bookName: '书名书名',
                            univalence: '176',          // 单价
                            bookType: '32开标准本',
                            editType: '自编辑',
                            count: 2,
                            pageCount: '96P',
                            bookSize: '144*192mm',
                        },
                        {
                            imgSrc: '',                 // 作品封面
                            bookName: '书名书名',
                            univalence: '176',          // 单价
                            bookType: '32开标准本',
                            editType: '自编辑',
                            count: 1,
                            pageCount: '96P',
                            bookSize: '144*192mm',
                        }
                    ],
                    freight: '12',                      // 运费    
                    totalCount: '10',                   // 共计件数
                    totalPrice: '188.00',               // 小计
                    cashCodeDiscount: '0.00',           // 现金码优惠
                    balance: '198.00',                  // 余额
                    realPay: '188.00',                  // 实付款  (受现金码优惠丶运费等影响)

                    
    }

    /mobile/settlement/payment            //  确认支付  复用公众号接口  细节再做交流
    


8. 图库    
    /mobile/gallery/getImgList            // 获取用户图库所有图片
    参数
    {
        openId: 'adwafawwafawfwafafwa'
    }
    响应数据
    {
        imgList: [
                    {
                        imgSrc: '',       // 图片src
                        dataIndex: '1001',  // 图片标识，删除 移动 填图 套图 等操作以dataIndex作为参数
						isSelect: false,      // 写死
                    },
                    {
                        imgSrc: '',       // 图片src
                        dataIndex: '1002',  // 图片标识，删除 移动 填图 套图 等操作以dataIndex作为参数
						isSelect: false,
                    },
                ]
    }

    /mobile/gallery/getGroups       // 获取用户图库图片所有自定义分组
    参数
    {}
    响应数据
    {
        groupList: [
            {
                groupName: '全部图片',    // 分组名
                imgNum: '321'           //  分组包含图片数量
                dataIndex: '01'         // 分组标识
            },
            {
                groupName: 'Big Ben',    // 分组名
                imgNum: '200'           //  分组包含图片数量
                dataIndex: '02'
            }
        ]
    }

    /mobile/gallery/addGroup       // 新建分组
    参数
    {}
    响应数据
    {
        200
    }

    /mobile/gallery/moveGroup       // 图片移入分组
    参数
    {
        currentGroup: '01',                 // 01: 分组标识dataIndex
        imgList: [1003,1016,1009,1010]      // 数组元素: 图片dataIndex
        targetGroup: '02'
    }


    /mobile/gallery/deleteImg       // 删除图库图片
    参数
    {
        dataIndex: groupDataIndex,      // 当前分组标识
        imgList: [1001,1002]            // 当前分组选中的图片dataIndex
    }
    响应数据
    {
        200
    }

    /mobile/gallery/fillingImg       // 一件套图    公众号接口直接复用(细节再做交流)



9. 所有产品
    /mobile/classification/getNavList            // 获取所有产品信息
    参数
    {}
    响应数据
    {
        navList: [
            // ------------------------------照片书-------------------------------
                    {
                        text:'照片书',
                        isActive:true,
                        produceTitle: '自编辑产品',
                        produceTips: '您可以选择以下产品并在壹本印画编辑平台上编辑作品，体验自己创作的乐趣。',
                        background: 'orange',
                        productList: [
                            {
                                // 32开标准本
                                title: '32开标准本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    },
                                    {
                                        imgSrc: '',
                                        text: '壹本情书',
                                        price: 138
                                    }
                                ]
                            },
                            {
                                // 精装布面本
                                title: '精装布面本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    },
                                    {
                                        imgSrc: '',
                                        text: '壹本情书',
                                        price: 138
                                    },
                                    {
                                        imgSrc: '',
                                        text: '壹本情书',
                                        price: 138
                                    },
                                    {
                                        imgSrc: '',
                                        text: '壹本情书',
                                        price: 138
                                    }
                                ]
                            },
                            {
                                // MOOK
                                title: 'MOOK',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    }
                                   
                                ]
                            },
                            {
                                // 对裱写真本
                                title: '对裱写真本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    },
                                    {
                                        imgSrc: '',
                                        text: '壹本情书',
                                        price: 138
                                    }
                                ]
                            },
                            {
                                // 软皮映画本
                                title: '软皮映画本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    },
                                    {
                                        imgSrc: '',
                                        text: '壹本情书',
                                        price: 138
                                    }
                                ]
                            },
                            {
                                // 精装映画本
                                title: '精装映画本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    },
                                    {
                                        imgSrc: '',
                                        text: '壹本情书',
                                        price: 138
                                    }
                                ]
                            },
                            {
                                // 原画影刊本
                                title: '原画影刊本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    }
                                    
                                ]
                            },
                        ]
                    },
                    
                    // ------------------------------小日志-------------------------------
                    {
                        text:'小日志',
                        isActive:false,
                        produceTitle: '自编辑产品',
                        produceTips: '您可以选择以下产品并在壹本印画编辑平台上编辑作品，体验自己创作的乐趣。',
                        background: 'orange',
                        productList: [
                            {
                                // 
                                
                            }
                        ]
                    },
                    
                    // ------------------------------明信片-------------------------------
                    {
                        text:'明信片',
                        isActive:false,
                        produceTitle: '自编辑产品',
                        produceTips: '您可以选择以下产品并在壹本印画编辑平台上编辑作品，体验自己创作的乐趣。',
                        background: 'orange',
                        productList: [
                            {
                                // 
                                
                            }
                        ]
                    },
                    
                    // ------------------------------手账本-------------------------------
                    {
                        text:'手账本',
                        isActive:false,
                        produceTitle: '自编辑产品',
                        produceTips: '您可以选择以下产品并在壹本印画编辑平台上编辑作品，体验自己创作的乐趣。',
                        background: 'orange',
                        productList: [
                            {
                                // 
                                
                            }
                        ]
                    },
                    
                    // ------------------------------台历-------------------------------
                    {
                        text:'台历',
                        isActive:false,
                        produceTitle: '自编辑产品',
                        produceTips: '您可以选择以下产品并在壹本印画编辑平台上编辑作品，体验自己创作的乐趣。',
                        background: 'orange',
                        productList: [
                            {
                                // 
                                
                            }
                        ]
                    },
                    
                    // ------------------------------联名款-------------------------------
                    {
                        text:'联名款',
                        isActive:false,
                        produceTitle: '自编辑产品',
                        produceTips: '您可以选择以下产品并在壹本印画编辑平台上编辑作品，体验自己创作的乐趣。',
                        background: 'orange',
                        productList: [
                            {
                                // 
                                
                            }
                        ]
                    },
                    
                    // ------------------------------批量定制-------------------------------
                    {
                        text:'批量定制',
                        isActive:false,
                        produceTitle: '批量定制服务',
                        produceTips: '个人/团体/企业客户的定制数量需求，壹本印画都有适合您的解决方案。',
                        background: 'black',
                        bottomTips: {
                            title: '大订单服务',
                            height: 'bottomTips450',
                            text: [
                                '如需订购500份或者更多数量的产品，请联系我们获取专属解决方案。',
                                '印刷和运输大约需要3至6周。',
                                '详情请联系客服代表壹朵'
                            ],
                            qrcode: ''
                        },
                        productList: [
                            {
                                // 
                                
                            }
                        ]
                    },
                    
                    // ------------------------------设计服务-------------------------------
                    {
                        text:'设计服务',
                        isActive:false,
                        produceTitle: '设计师服务',
                        produceTips: '选择产品并将文件打包上传，我们将为您提供设计师排版服务，省时省心。',
                        background: 'green',
                        bottomTips: {
                            title: '团体/企业定制',
                            height: 'bottomTips400',
                            text: [
                                '如需团体/企业客户设计及批量定制服务，请联系我们获取专属解决方案。',
                                '详情请联系客服代表壹朵'
                            ],
                            qrcode: ''
                        },
                        productList: [
                            {
                                // 32开标准本
                                title: '32开标准本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    }
                                   
                                ]
                            },
                            {
                                // 精装布面本
                                title: '精装布面本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    }
                                   
                                ]
                            },
                            {
                                // MOOK
                                title: 'MOOK',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    }
                                   
                                ]
                            },
                            {
                                // 精装映画本
                                title: '精装映画本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    }
                                   
                                ]
                            },
                            {
                                // 原画影刊本
                                title: '原画影刊本',
                                productOptionsList: [
                                    {
                                        imgSrc: '',
                                        text: '32开标准本',
                                        price: 138
                                    }
                                   
                                ]
                            }
                        ]
                    }
        ]
    }


10. 账单明细
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


11. 订单页
    /mobile/order/getList           // 获取订单页各种状态下卡片数据
    参数
    {}
    响应数据
    {
        list: [
                // 全部
                [
                    {
                        orderId: 8848,
                        orderStauts: '待付款',
                        specList: [
                            {
                                bookName: '书名书名',
                                univalence: '176',          // 单价
                                bookType: '32开标准本',
                                editType: '自编辑',
                                count: 1,
                                pageCount: '96P',
                                bookSize: '144*192mm',
                            }
                        ],
                        totalNum: 1,
                        totalPrice: 188.00,
                        freight: 12.00,             // 运费
                    },
                    {
                        orderId: 8849,
                        orderStauts: '待收货',
                        specList: [
                            {
                                bookName: '无感',
                                univalence: '176',          // 单价
                                bookType: '32开标准本',
                                editType: '自编辑',
                                count: 1,
                                pageCount: '96P',
                                bookSize: '144*192mm',
                            },
                            {
                                bookName: '哈哈',
                                univalence: '176',          // 单价
                                bookType: '32开标准本',
                                editType: '自编辑',
                                count: 2,
                                pageCount: '120P',
                                bookSize: '144*192mm',
                            }
                        ],
                        totalNum: 1,
                        totalPrice: 188.00,
                        freight: 12.00,             // 运费
                    }
                ],
                // 待付款
                [
                    {
                        orderId: 8850,
                        orderStauts: '待付款',
                        specList: [
                            {
                                bookName: '书名书名',
                                univalence: '176',          // 单价
                                bookType: '32开标准本',
                                editType: '自编辑',
                                count: 1,
                                pageCount: '96P',
                                bookSize: '144*192mm',
                            }
                        ],
                        totalNum: 1,
                        totalPrice: 188.00,
                        freight: 12.00,             // 运费
                    },
                    {
                        orderId: 8851,
                        orderStauts: '待付款',
                        specList: [
                            {
                                bookName: '无感',
                                univalence: '176',          // 单价
                                bookType: '32开标准本',
                                editType: '自编辑',
                                count: 1,
                                pageCount: '96P',
                                bookSize: '144*192mm',
                            },
                            {
                                bookName: '哈哈',
                                univalence: '176',          // 单价
                                bookType: '32开标准本',
                                editType: '自编辑',
                                count: 2,
                                pageCount: '120P',
                                bookSize: '144*192mm',
                            }
                        ],
                        totalNum: 1,
                        totalPrice: 188.00,
                        freight: 12.00,             // 运费
                    }
                ],
                // 待发货
                [],
                // 已完成
                [],
                // 活动
                []
            ]
    }

    /mobile/order/confirmReceipt           // 确认收货 (复用公众号接口  细节再做交流)
    参数
    {}
    响应数据
    {
        200
    }

    /mobile/order/addon           // 加印作品  (复用公众号接口  细节再做交流)
    参数
    {}
    响应数据
    {
        200
    }

    <!-- /mobile/order/checkLogistics            // 查看物流   
    参数
    {
        logisticsId : 'YT4307602353777'          // 物流号
    }
    响应数据
    {

    } -->



    12. 首页
    /mobile/index/indexInfo        
    参数
    {}
    响应数据
    {
        // 首页banner列表
        bannerList: [
                    {
                        img:'',
                        text: 'A',
                        color:'red'
                    },
                    {
                        img:'',
                        text: 'B',
                        color:'skyblue'
                    },
                    {
                        img:'',
                        text: 'C',
                        color:'oranged'
                    }
                ],


        // 首页news
        newsInfo: {
            text: '【NEWS】莫兰迪油白系列上新，限时88折 ',
            link: 'http://abwfuwhalfiawhflwalfahfilawhifaw',        
        },

        // 壹本精选
        choiceness: [
                    {
                        imgSrc: '',     // 产品封面图
                        link: '',       // 对应产品跳转链接   （再做讨论）
                    },
                    {
                        imgSrc: '',     // 产品封面图
                        link: '',       // 对应产品跳转链接   （再做讨论）
                    },
                    {
                        imgSrc: '',     // 产品封面图
                        link: '',       // 对应产品跳转链接   （再做讨论）
                    },
                    {
                        imgSrc: '',     // 产品封面图
                        link: '',       // 对应产品跳转链接   （再做讨论）
                    }
                ]



        // 场景数据
        cardList:[
                    // 摄影
                    [
                        {
                            imgSrc: '',         // 产品封面
                            typeName: '精装布面本',  // 产品名
                            price: '399',           // 产品价格 ： 1.范围 288-399则页面展示 288起   2.399  
                        },
                        {
                            imgSrc: '',         // 产品封面
                            typeName: '软皮映画本',  // 产品名
                            price: '278',           // 产品价格 ： 1.范围 288-399则页面展示 288起   2.399  
                        },
                        {
                            imgSrc: '',         // 产品封面
                            typeName: '音乐手账',  // 产品名
                            price: '399',           // 产品价格 ： 1.范围 288-399则页面展示 288起   2.399  
                        },
                        {
                            imgSrc: '',         // 产品封面
                            typeName: '2020艺术家台历',  // 产品名
                            price: '399',           // 产品价格 ： 1.范围 288-399则页面展示 288起   2.399  
                        }
                    ],
                    
                    // 旅游   数据格式同上
                    [],
                    //毕业
                    [],
                    //爱情
                    [],
                    // 亲子
                    []
                ]
    }


    13. 产品详情界面
    /mobile/classification/getProductDetailsInfo            // 产品详情界面加载获取对应产品信息
    参数
    {
        productId: '03'         // 全部产品 产品分类界面点击对应产品card 页面传参产品id   请求接口获取信息
    }
    响应数据
    {
        // 轮播banner 
        swiperItemList: [
                    {
                        bannerSrc: ''
                    },
                    {
                        bannerSrc: ''
                    },
                    {
                        bannerSrc: ''
                    }
                ],

        // 对应产品尺寸
        size: '170×225MM',
        desc: '每个人都能拥有的大师级自出版作品',           // 对应产品描述简介

        // 选择规格弹窗多规格
        specsList:[         
                    {
                        spec: '80P',
                        price: '￥188'   // 对应规格价格
                    },
                    {
                        spec: '120P',
                        price: '￥388'   // 对应规格价格
                    },
                    {
                        spec: '140P',
                        price: '￥256'   // 对应规格价格
                    }
                ],

        // 产品详情图
        productDetailsImgList: [
                    {
                        imgSrc: ''
                    },
                    {
                        imgSrc: ''
                    },
                    {
                        imgSrc: ''
                    },
                    {
                        imgSrc: ''
                    }
                ]
    }




    13. 公共搜索页面
    /mobile/search/getHotKeywordList        // 获取用户热门搜索关键词   (不好做就不做  具体和alice讨论一下)
    参数
    {}
    响应数据
    {
        hotKeywordList: ['键盘', '鼠标', '显示器', '电脑主机', '蓝牙音箱', '笔记本电脑', '鼠标垫', 'USB', 'USB3.0']
    }


    /mobile/search/getGoodsInfo             // 根据用户输入关键词搜索相关产品  模糊查询
    参数
    {
        userInputText: '文艺肖方册'
    }
    响应参数
    {
        goodsList: [
            {
                imgSrc: '',                 // 产品封面
                bookName: '文艺小方册',
                price: '378'
            }
        ]
    }



    /mobile/search/getRecommendList             // 为你推荐 产品列表
    参数
    {}
    响应数据
    {
        recommendList : [
            {
                imgSrc: '',                 // 产品封面
                bookName: '文艺小方册',
                price: '378'
            },
            {
                imgSrc: '',                 // 产品封面
                bookName: '软皮映画本',
                price: '322'
            },
            {
                imgSrc: '',                 // 产品封面
                bookName: '精装布面大开本',
                price: '128'
            }
        ]
    }



    14. 编辑列表页
    /mobile/editor/getPagesList             // 获取九宫格编辑列表页书本page列表
    参数
    {
        bookId: '1231'      // 书本id
    }
    响应数据
    {
        pagesList: [
					// 固定页 列表
					[
						{
							data_type: 'COVER',
							data_type_name: '封面',
							data_id: '168785',
							imgSrc: ''
						},
						{
							data_type: 'TITLE',
							data_type_name: '扉页',
							data_id: '168785',
							imgSrc: ''
						},
						{
							data_type: 'BLANK',
							data_type_name: '空白页',
							data_id: '168785',
							imgSrc: ''
						}
					],
					// 正文 列表
					[
						{
							data_type: 'CONTENT',
							data_type_name: '正文',
							data_id: '168785',
							imgSrc: ''
						},
						{
							data_type: 'CONTENT',
							data_type_name: '正文',
							data_id: '168785',
							imgSrc: ''
						},
						{
							data_type: 'CONTENT',
							data_type_name: '正文',
							data_id: '168785',
							imgSrc: ''
						},
					],
					// 固定页 列表
					[
						{
							data_type: 'COPYRIGHT',
							data_type_name: '版权页',
							data_id: '168785',
							imgSrc: ''
						},
						{
							data_type: 'BOTTOM',
							data_type_name: '封底',
							data_id: '168785',
							imgSrc: ''
						},

					],
					
				]
    }



    15. 预览页
    /mobile/preview/getBookInfo             // 获取书本信息
    参数
    {
        bookId: '1256'
    }
    响应数据
    {
        // 书本 书名规格等信息
        bookName: '小甜豆'
        bookType: '32开标准本',
		bookSpec: '92P',

        // 书本每一页信息
        swiperList: [       
					{
						imgSrc: '',
						data_type: 'COVER'
					},
					{
						imgSrc: '',
						data_type: 'TITLE'
					},
					{
						imgSrc: '',
						data_type: 'BLANK'
					},
					{
						imgSrc: '',
						data_type: 'CONTENT'
					},
					{
						imgSrc: '',
						data_type: 'COPYRIGHT'
					},
					{
						imgSrc: '',
						data_type: 'BOTTOM'
					}
				]
    }







