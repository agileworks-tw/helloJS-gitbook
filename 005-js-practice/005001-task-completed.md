# Task 新增紀錄 Task 的完成狀態

## Story

為了讓使用者知道 Task 還有哪些項目待處理，需要紀錄 Task 的完成狀態。

## 步驟

* model Task 新增 completed 欄位紀錄 Task 是否被完成
* 撰寫 test case 確認更新 model Task completed 成功
* 新增 test 定義 task 更新 completed 之 API spec
* 實作 Task completed 更新 API 並且透過 test 驗證 API
* 調整後端頁面顯示 completed 的值
* 調整前端針對 completed 的變動，呼叫完成的 API 
* 確認在前端調整的 completed 之變動，在後端看到的是相同的變動


## 測試方式

1. 開啟前台畫面，新增 task，可以正確新增
2. 新增 task 後，task 將可以識別該 task 是否已完成
3. 假設新增 task 成功，進入後台，可以看到該使用者的特定 Task 狀態為已完成
4. 若再次在前台變更完成狀態為未完成，則可以在後台看到顯示該 Task 顯示為未完成

