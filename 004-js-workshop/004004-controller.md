# Controller


## 實作透過 api 取得特定 user 之所有 task list 資料


根據上一章節 測試案例 API 的定義：

```
  it('透過 api 取得特定 user 之所有 task list 資料', async function () {
    // 建立測試資料
    let username = 'johndoe';
    let user = await this.models.User.create({
      username
    });
    
    await this.models.Task.create({
      title: 'johndoe task',
      UserId: user.id
    });

    // 呼叫 API 取得資料
    let response = await request(app).get(`/api/users/${username}/tasks`);
    let result = response.body;

    // 確認資料結構
    expect(result.tasks).to.be.an('array');
    expect(result.tasks[0])
      .to.be.an('object')
      .and.to.have.property("title");
  });

```

撰寫對應的 API 程式如下

```
router.get('/api/users/:user_name/tasks', async function (req, res) {
  // 取得 api path 之參數 user_name 的值
  let username = req.params.user_name;

  // 透過 user_name 查詢 user 資料取得 user 識別 id
  let user = await models.User.findOne({
    where: {username}
  });
  let UserId = user.id;

  // 透過 user 識別 id 取得該使用者所有的 task 資料
  let tasks = await models.Task.findAll({
    where: {UserId}
  });

  // 回傳查詢結果透過 json 的形式
  res.json({tasks});

});

```

運行下面指令

`npm run test-integration`

將會出現下面訊息


```
    ✓ 透過 api 取得特定 user 之所有 task list 資料 (53ms)
    1) 透過 api 新增特定 user 之 task 資料


  1 passing (343ms)
  1 failing
```

第一項 spec 已通過，確認 API 已實作完成，接著下一節完成另一個 API 實作


## 實作透過 api 新增特定 user 之 task 資料


根據上一章節 測試案例 API 的定義：

```
  it('透過 api 新增特定 user 之 task 資料', async function () {

    // 建立測試資料
    let username = 'andy';
    await this.models.User.create({
      username
    });

    let taskData = {
      title: "andy task"
    }

    // 呼叫 API 新增 task
    let response = await request(app)
      .post(`/api/users/${username}/tasks/create`)
      .send(taskData);
    let result = response.body;
    
    // 確認資料結構
    expect(result.task)
      .to.be.an('object')
      .and.to.have.property("title");
  });



```

撰寫對應的 API 程式如下

```

router.post('/api/users/:user_name/tasks/create', async function (req, res) {

  // 取得 api path 之參數 user_name 的值
  let username = req.params.user_name;

  // 透過 user_name 查詢 user 資料取得 user 識別 id
  let user = await models.User.findOne({
    where: {username}
  });

  // 取得送給 api 之更新資料 title 的值，並建立 task 關聯給 user
  let title = req.body.title;
  let task = await models.Task.create({
    title,
    UserId: user.id
  })

  // 回傳查詢結果透過 json 的形式
  res.json({task});
});

```

運行下面指令

`npm run test-integration`

將會出現下面訊息

```
    ✓ 透過 api 取得特定 user 之所有 task list 資料 (55ms)
    ✓ 透過 api 新增特定 user 之 task 資料
```

到此已完成 API 的撰寫，可以進入前端進行整合


