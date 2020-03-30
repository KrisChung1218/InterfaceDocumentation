# 壹本印画小程序


------------------------------------------------------------ 接口部分 --------------------------------------------------------
1. 购物车   
    <!-- /mobile/cart/getOrderList		查询购物车卡片数据
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
        
    } -->

    /mobile/cart/delteCard		删除购物车卡片
    参数
    {
        //dataIndex: dataIndex  // 卡片对应标识dataIndex
        id: 查询接口返回,
        type: 查询接口返回,
        quant: 0 //0-修改数量，删除产品
        openId: ‘12149212148’  用户微信openid
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
    {
    openId: ‘12149212148’  用户微信openid
    }
    响应数据
    {
        200
    }

//删除接口，一起合并到/mobile/personal/getWalletInfo
    /mobile/personal/checkBalance          查询钱包余额(用户每次进入个人中心都会调用查询)
    参数
    {
    openId: ‘12149212148’  用户微信openid
    }
    响应数据
    {
        balance: '180.00'       
    }



    


<!-- 3. 团购列表
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
    参考：https://test.yibenprint.com/mobile/groupon/getNavList/ 的返回数据 -->


<!-- 4. 团购详情    
    /mobile/groupon/getDetailsInfo          // 获取团购列表卡片对应详情数据
    参数
    {
        grouponCardId: ''    (string)
    }
    响应数据
    参考：https://test.yibenprint.com/mobile/groupon/getDetailsInfo/191 的返回数据
    
    {
        detailsInfo: {
            bannerImgList: ['','',''],					// banner 图片路径
			soldNum: 33,								// 已售件数
			productDetailsImgList: ['','','','','','']	// 产品详情图片路径			
		}
    } -->




5. 我的书架   



    /mobile/bookshelf/getWorksList            // 获取我的书架卡片数据(无则返回空对象)
    参数
    {
    orderPageIn: 1 // 可不传，1-订单页进去的
    spec_id: 123 // orderPageIn=1时才需要传
    tree_id: 123 //作品下拉框的id， 选择全部作品时不需要传
    }
    响应数据
    参考：https://test.yibenprint.com/mobile/bookshelf/getWorksList/ ,如果是订单页进去的在末尾加上：orderPageIn-1__spec_id-规格id，过滤掉其他规格
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
					
        ]
    }



    /mobile/bookshelf/getAllWorksOptionsList            // 获取下拉框分类数据
    参数
    {}
    响应数据
    参考：https://test.yibenprint.com/mobile/bookshelf/getAllWorksOptionsList/
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
    /mobile/personal/getWalletInfo           // 获取用户余额
    参数
    {
        openId: 'gaghlawigl2ih3li',          // 用户数据表主键,是否为openId?
    }
    响应数据
    {
        balance: '180.00',
        isOpen: ture                        // 用户是否开通钱包标识   false  true || '0' '1'   
    }


//删除接口，合并到/mobile/personal/getWalletInfo

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
         // openId: 'gagwagagwagawgga'                  //有cookie不需要传openid
    }
    响应数据
    参考   /mobile/settlement/getUserReceiptInfoList 
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
        ],
    }


    /mobile/settlement/getSettlementInfo            // 获取用户结算信息
    参数
    {
        book_num: 0 // 单个团购规格包含的书籍数量
        source // cart-购物车，addon-加印，buy-立即购买，
        items:{     // source为cart,addon的情况传，
            id: //sku_id
            type: // sku_type
            quantity : // 加印传，其他不传
        }
        item：// //sku_id， source为buy的情况传，
        type: // sku_type， source为buy的情况传
        quantity //数量 ，source为buy的情况传
        discountCode // 现金码
        
    }
    响应数据
    参考 /mobile/settlement/getSettlementInfo


创建新书，参考原来的接口
/pceditor/ajax/create_new_book/
团购创建新书，参考原来的接口
/m/ajax/create_new_book_groupon/


    /mobile/settlement/payment            //  确认支付  复用公众号接口  细节再做交流
    

8. 图库    
    /mobile/gallery/getImgList            // 获取用户图库所有图片
    参数
    {
        tag_id: 图片分类id（分组id），不传查询全部图片
    }
    响应数据
    参考：/mobile/gallery/getImgList/tag_id-134 // 134是用户jimmy的图库分组id，请填你自己的
    {
        tag: // 当前分类
        list // 图片列表
        tag_list // 分类统计列表
        all_count // 全部图片数
    }

//---- 上面的接口包含了这个接口的返回数据
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

    /mobile/gallery/addGroup       // 新建分组   使用原来的  /home/ajax/create_new_tag/
    参数
    {}
    响应数据
    {
        200
    }

    /mobile/gallery/moveGroup       // 图片移入分组    使用原来的  /home/ajax/move_user_images/
    参数
    {
        currentGroup: '01',                 // 01: 分组标识dataIndex
        imgList: [1003,1016,1009,1010]      // 数组元素: 图片dataIndex
        targetGroup: '02'
    }


    /mobile/gallery/deleteImg       // 删除图库图片    使用原来的  /home/ajax/delete_user_tag/
    参数
    {
        dataIndex: groupDataIndex,      // 当前分组标识
        imgList: [1001,1002]            // 当前分组选中的图片dataIndex
    }
    响应数据
    {
        200
    }
    
    修改分组名称接口：    使用原来的  /home/ajax/name_user_tag/
    
    
    

    /mobile/gallery/fillingImg       // 一件套图    公众号接口直接复用(细节再做交流)



9. 所有产品
    /mobile/classification/getNavList            // 获取所有产品信息
    参数
    {}
    响应数据
    参考：https://test.yibenprint.com/mobile/classification/getNavList/ 的返回，里面是树状结构，有递归
    
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
                ]
            },
                    
        ]
    }

10. 账单明细
充值账单
/mobile/personal/getChargeWalletInfo/    GET请求
参数
{
    type //状态(ALL,UNPAY,PAYED),
    page 当前页码
    pageSize 每页数量
}

交易流水
/mobile/personal/walletLog/    GET请求
参数
{
    type //状态(ALL,OUT,IN),
    page 当前页码
    pageSize 每页数量
}
   

11. 订单页
    /mobile/personal/orderList           // 获取订单页各种状态下卡片数据
    参数
    {
    status ：状态（wait_payment-待支付，wait_file-待上传， wait_deliver-代发货，delivered-已发货待收货，finished-已完成
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
                    ],
                    
                    // 旅游   数据格式同上
                    [],
                ]
    }


    13. 产品详情界面
    /mobile/classification/getProductDetailsInfo            // 产品详情界面加载获取对应产品信息
    参数
    {
        cat_id: '45'         // 全部产品 产品分类界面点击对应产品card 页面传参产品id   请求接口获取信息
    }
    响应数据
    参考：https://test.yibenprint.com/mobile/classification/getProductDetailsInfo/cat_id-45 //45是产品id，get请求
    {
        // 轮播banner 
        swiperItemList: [
                    {
                        bannerSrc: ''
                    },
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
                ],

        // 产品详情图
        productDetailsImgList: [
                    {
                        imgSrc: ''
                    },
                ]
    }


//   -----------------------------------flag---------------------------

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
        ]
    }


//=========
    <!-- 14. 编辑列表页
    /mobile/editor/getPagesList             // 获取九宫格编辑列表页书本page列表
    参数
    {
        id: '1231'      // 书本id
    }
    响应数据
    {
        pagesList: [
            {
                data_type: 'COVER',
                data_type_name: '封面',
                data_id: '168785',
                imgSrc: ''
            },
    } -->



    15. 预览页
    /mobile/editor/preview/             // 获取书本信息
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
				]
    }







