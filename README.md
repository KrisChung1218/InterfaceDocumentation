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
                    // tabTitle 导航栏第一个模块页面卡片数据  tabTitle:['照片书','热门活动'], 
                    [
                        {
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
                    []
                ]
    }






