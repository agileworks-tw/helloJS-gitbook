# Summary

* [Introduction](README.md)

* 01 現代軟體開發工法
    * MVC 分層開發觀念
    * TDD 測試驅動開發
    * DevOps 觀念概論
    * 前後端分離開發

* 為什麼要學 JavaScript
    * JavaScript 的至今發展狀況
    * JavaScript 應用案例

* 範例專案說明
    * [初始專案與專案說明](./004-js-workshop/004001-install.md)
    * [model: ORM 透過程式碼定義資料庫](./004-js-workshop/004002-model.md)
    * [test: 透過測試確認 model 定義運作正常，即定義 API spec](./004-js-workshop/004003-test.md)
    * [controller: 實作 API 並且透過 test 驗證 API](./004-js-workshop/004004-controller.md)
    * [view: 前後端整合測試](./004-js-workshop/004005-view.md)

* JavaScript 動手做
    * Task 新增 completed 欄位紀錄 Task 是否被完成
    * 撰寫 test case 確認更新 completed 成功
    * 新增 test 定義 task 更新 completed 之 API spec
    * 實作 Task completed 更新 API 並且透過 test 驗證 API
    * 調整後端頁面顯示 completed 的值
    * 調整前端針對 completed 的變動，呼叫完成的 API 
    * 確認在前端調整的 completed 之變動，在後端看到的是相同的變動
