# Input 元素属性


| Input 类型            | 功能说明                | 浏览器不支持时行为                | 备注                        |
| ------------------- | ------------------- | ------------------------ | ------------------------- |
| `color`             | 颜色选择器，弹出色盘          | 显示为普通文本框，用户可手动输入颜色代码     | 如：`#FF0000`               |
| `date`              | 日期选择器（年-月-日）        | 显示为文本输入框                 | 不含时区信息                    |
| `datetime-local`    | 日期+时间选择器（不含时区）      | 显示为文本框，用户手动输入            | Chrome 显示为日历+时间控件         |
| `email`             | 输入邮箱，自动校验格式         | 显示为普通文本框，无自动校验           | 需符合邮箱格式                   |
| `number`            | 仅数字输入，可设置最小值、最大值、步长 | 显示为普通文本框                 | 可用上下箭头调整                  |
| `range`             | 滑块控件，选择数值范围         | 显示为普通文本框                 | 默认不显示数值，需 JavaScript 显示   |
| `search`            | 搜索框，外观略异            | 显示为普通文本框                 | 支持搜索历史记录（WebKit 浏览器）      |
| `tel`               | 电话号码输入框，不强制格式校验     | 显示为普通文本框                 | 可用 `pattern` 自定义校验        |
| `url`               | URL 输入，自动格式校验       | 显示为普通文本框                 | 必须输入有效网址格式                |
| `list` + `datalist` | 自动完成提示列表            | 若不支持 `datalist`，显示为普通输入框 | `option` 嵌套于 `datalist` 中 |
| `placeholder`       | 显示示例文本作为提示          | 支持差异较小                   | 不提交 placeholder 本身为表单值    |
| `required`          | 标记输入为必填项            | 若浏览器不支持则无效               | 可用 JavaScript 实现验证回退逻辑    |

### number & range

```html
<input type="number" min="5" max="10">
```

### tel：

```html
<input type="tel" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
```

### list + datalist

![image.png](gerry-cs-journal/stack-learning-notes/HTML/src/Input%20元素属性/image.png)

可以自动完成，但是仍然可以自定义输入

```html
<input type="text" list="fruit">
<datalist id="fruits">
	<option value="apple"></option>
	<option value="bananas"></option>
	<option value="oranges"></option>
</datalist>
```

## attribute:

### placeholder

显示示例文本作为提示

### required

使得该项为必填项

```html
<input type="email" placeholder="example@email.com" required>
```