# Magento1.x 常見配置與使用情境

## 資料表操作與資料取得

```php
// Model 名稱參考 config.xml 定義，models 標籤
$model = Mage::getModel('catalog/product');
$collection = $model->getCollection();
// 合併資料表查詢
// join([要合併查詢的資料表], 關聯條件，額外查詢的資料表欄位)
$collection->join(
    ['account'=> 'affiliateplus/account'],
    'account.account_id = main_table.tier_id',
    ['account.identify_code as tier_identify_code']
);

// 取得第一筆資料
$item = $collection->getFirstItem()->getData();
// 查詢單一欄位
$model->load('123', 'order_id');
// 條件查詢
$collection->addFieldToFilter('product_id', 1);
// 套用 API 查詢時的欄位條件 (參考 config.xml 欄位定義)
$this->_applyCollectionModifiers($collection);
// 篩選欄位資料於 EAV 模組資料表 (product, customer, salesorder)
$collection->addAttributeToFilter('status', Mage_Catalog_Model_Product_Status::STATUS_ENABLED);
// 篩選欄位資料於一般資料表
$collection->addFieldToFilter('product_id', 1);

// 群組欄位
$collection->getSelect()->group('main_table.customer_id');

// 從資料庫取得物件後，拿出物件資料
$item->getData();
// 取得特定屬性資料，注意 get 後面接的屬性名稱要用大駝峰式命名
$item->getId();
$item->getName();
// 從 $collection 取得每筆資料
$result = [];
foreach ($collection as $item) {
    $result[] = $item->getData();
}

// 存入資料
$model->setName('name');
$model->setType('type');
$model->save();
```

