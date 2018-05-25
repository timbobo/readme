# 一致性控件使用Wiki

## 1.滚动条一致性(含有ListView，RecyclerView等滚动属性的界面
在该界面主题中，添加如下属性：<br>
```
<item name="android:scrollbarThumbVertical">@drawable/scrollbar_handle_material_padding</item>
```

## 2.TabLayout的文字在英文下大小写
在TabLayout的布局中，加入如下属性:<br>
```
app:tabTextAppearance="@style/TabViewStyleTP"
```

## 3.AlertDialogTP
删除setTPMode接口，将原先的AlertDialog替换成AlertDialogTP即可。
<br>

## 4.NumberPickerTP
将原先import的android.widget.NumberPickerTP替换成TPWidgets中的NumberPickerTP即可，将反射修改颜色的方法替换成新增方法。<br>
**新增方法**：
```
/**
* 设置NumberPickerTP的颜色
* 
* @param color
*/
public void setTextColor(@IdRes int color)
```
**方法修改**：
```
private void changeValueByOne(boolean increment)  -> public void changeValueByOne(boolean increment)
```

## 5.TimePickerTP
删除原先带有判断变量的构造函数，将TimerPicker替换成TimerPickerTP即可。<br>
**新增方法**：<br>
```
/**
* 设置TimerPickerTP的颜色
*
* @param color
*/
public void setTextColor(@IdRes int color)
```

## 6.DatePickerTP
删除原先带有判断变量的构造函数，将DatePicker替换成DatePickerTP即可。<br>
**新增方法**：<br>
```
/**
* 设置DatePickerTP的颜色
*
* @param color
*/
public void setTextColor(@IdRes int color)
```
## 7.自研水滴滑块SeekBarTP
将原来的SeekBar替换成SeekBarTP即可，其余不变。<br>
<br>
## 8.搜索一致性SearchViewTP
直接替换成SearchViewTP即可，若在menu中使用，改为```app:actionViewClass="com.tplink.widget.SearchViewTP" ```。
删除之前反射修改CursorDrawable，HintTextColor，SearchButton的方法，替换为新增的方法<br>
**新增方法**：
```
/**
* set the cursor color of the search text<br>
* @param resId
*/
public void setCursorDrawableRes(@DrawableRes int resId)<br>

/**<br>
* set the hint text color with color value<br>
* @param color<br>
*/<br>
public void setHintTextColor(int color)<br>

/**
* set the hint text color with color res
* @param resId
*/
public void setHintTextColorRes(@ColorRes int resId)

/**
* set the button drawable with drawable
* @param drawable
*/
public void setSearchButtonDrawable(Drawable drawable)

/**
* set the button drawable with drawable res
* @param resId
*/
public void setSearchButtonDrawableRes(@DrawableRes int resId)
```

## 9.DatePickerDialogTP，TimePickerDialogTP
将DatePickerDialog和TimePickerDialog替换即可，注意构造函数中删除判断变量。
<br>
<br>
## 10.溢出菜单自定义样式
增加了样式：@style/ActionModeTP,@style/SpinnerTP,@style/ContextPopupMenuTP分别用于不同类型的溢出菜单，应用替换即可。或者指定android:popupBackground属性为@drawable/spinner_background_roundrect_tp。
<br>
<br>
## 11. 标题栏图标一致性
在有标题栏的页面设置以下属性，用于统一标题栏返回键和溢出菜单键<br>
```
<item name="android:homeAsUpIndicator">@drawable/ic_ab_back_material</item>
<item name="android:actionModeCloseDrawable">@drawable/ic_ab_back_material</item>
<item name="android:actionOverflowButtonStyle">@style/ActionBarOverflowCloseDrawableStyleTP</item>
```
## 12.ProgressDialogTP
删除setTPMode接口，将原先的ProgressDialog替换成ProgressDialogTP即可。
<br>
