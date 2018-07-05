# Task 新增紀錄 Task 的完成狀態

## Story

為了讓使用者知道 Task 還有哪些項目待處理，需要紀錄 Task 的完成狀態。

## 步驟

### 後端調整

* model Task 新增 completed 欄位紀錄 Task 是否被完成

* migration 程序新增 model Task 欄位 completed

新增 migration 檔案指令

`node_modules/.bin/sequelize migration:create --name task-add-completed`


```
module.exports = {
up: (queryInterface, Sequelize) => {
    queryInterface.addColumn(
    'Todo',
    'completed',
    Sequelize.BOOLEAN
    );
},

down: (queryInterface, Sequelize) => {
    queryInterface.removeColumn(
    'Todo',
    'completed'
    );
}
};

```

執行下列指令更新 database

`node_modules/.bin/sequelize db:migrate`


* 撰寫 test case 確認更新 model Task completed 成功
* 新增 test 定義 task 更新 completed 之 API spec
* 實作 Task completed 更新 API 並且透過 test 驗證 API
* 調整後端頁面顯示 completed 的值

### 前端調整

* 調整前端針對 completed 的變動，呼叫完成的 API 



## 測試方式

1. 開啟前台畫面，新增 task，可以正確新增
2. 新增 task 後，task 將可以識別該 task 是否已完成
3. 假設新增 task 成功，進入後台，可以看到該使用者的特定 Task 狀態為已完成
4. 若再次在前台變更完成狀態為未完成，則可以在後台看到顯示該 Task 顯示為未完成

## 解答

### 後端

<https://github.com/agileworks-tw/express-example/pull/1>

### 前端

<https://github.com/agileworks-tw/express-example-vue/pull/1>