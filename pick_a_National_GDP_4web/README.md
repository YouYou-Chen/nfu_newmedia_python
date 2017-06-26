pick_a_zb_national

英文项目名称pick_a_zb_national
		
# 简介 
选取的国家PPPGDP，输入方面用户可用国家简称进行选择也可以使用下拉列表，输入出方面则是输出该国家1980年到2022年的PPPGDP值。


		
## 输入：

用户输入国家简称或者在点击下拉列表中所需的国家。

## 输出：

用户得到输出结果为：国家1980年到2022年的PPPGDP值，共42项数据输出，见[tempaltes/results.html](tempaltes/results.html)模版中table标签所包的数据。

## 从输入到输出，除了flask模块，本组作品还使用了：
### 模块
* 使用了[csv]、[tsv]、[pandas]，没有使用API

### 数据
* 数据来源为IMF数据库中的取得的xls档，用pandas将他转为tsv档[data/fsnd_national.tsv](data/fsnd_national.tsv)

### API
* 本组并未执行其他数据清理工作。

	
## Web App动作描述

以下按web 请求（web request） - web 响应 时序说明

1. 後端伺服器启动：执行 pick_a_zb_national.py 启动後端伺服器，等待web 请求。启动成功应出现：  * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)

2. 前端浏览器web 请求：访问 http://127.0.0.1:5000/ 启动前端web 请求

3. 後端伺服器web 响应：[pick_a_zb_national.py](pick_a_zb_national.py) 中 执行 了@app.route('/') 下的 entry_page()函数，以HTML模版[templates/entry.html](templates/entry.html)及一个含指标代码及名称的字典（见代码 the_list_items = c_list）产出的产生《欢迎来到网上查国家PPPGDP！》的HTML页面

4. 前端浏览器收到web 响应：出现HTML页面有HTML表单的输入 input 类型(type) 为"text"，变数名称(name)为'user_zb'，使用了HTML5的datalist 定义在 list="zbs" 及 datalist标签，详见HTML模版[templates/entry.html](templates/entry.html)

5. 前端浏览器web 请求：用户选取指标後按了提交钮「搞吧」，则产生新的web 请求，按照form元素中定义的method='POST' action='/pick_a_zb'，以POST为方法，动作为/pick_a_zb的web 请求

6. 後端服务器收到用户web 请求，匹配到@app.route('/pick_a_zb', methods=['POST'])的函数 pick_a_zb() 

7. [pick_a_zb_national.py](pick_a_zb_national.py) 中 def pick_a_zb() 函数，把用户提交的数据，以flask 模块request.form['user_zb']	取到Web 请求中，HTML表单变数名称user_zb的值，存放在user_zb这Python变数下，再使用flask模块render_template 函数以[templates/results.html](templates/results.html)模版为基础（输出），其中模版中the_zb的值，用user_zb这变数之值，其42项值如此类推。

8. 前端浏览器收到web 响应：模版中[templates/results.html](templates/results.html) 的变数值正确的产生的话，前端浏览器会收到正确响应，看到指标的相关元数据。



## 作者成员：
见[_team_/_team_.tsv](_team_/_team_.tsv)