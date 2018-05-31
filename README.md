# TPWidgets使用Wiki

## 控件库

### 1.AlertDialogTP
删除setTPMode接口，将原先的AlertDialog替换成AlertDialogTP即可。
<br>

### 2.NumberPickerTP
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

### 3.TimePickerTP
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

### 4.DatePickerTP
删除原先带有判断变量的构造函数，将DatePicker替换成DatePickerTP即可。<br>
**新增方法**：<br>
```
/**
* 设置DatePickerTP的颜色
*
* @param color
*/
public void setTextColor(@IdRes int color)

/**
* 隐藏头部显示日期的TextView
*/
public void hideTitle()

/**
* 显示头部显示日期的TextView
*/
public void showTitle()
```
### 5.自研水滴滑块SeekBarTP
将原来的SeekBar替换成SeekBarTP即可，其余不变。<br>
<br>
### 6.搜索一致性SearchViewTP
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

### 7.DatePickerDialogTP，TimePickerDialogTP
将DatePickerDialog和TimePickerDialog替换即可，注意构造函数中删除判断变量。
<br>
<br>
### 8.ProgressDialogTP
删除setTPMode接口，将原先的ProgressDialog替换成ProgressDialogTP即可。
<br>
<br>
<br>
## Preference库
新增了3个与Dialog相关的Preference类，**请在使用Preference的Activity或者Fragment的onDestroy里，手动调用xxxx(preference对象).onActivityDestroy()**
### 1.ListPreferenceTP
新增ListPreferenceTP，代码中直接替换ListPreference即可，在xml替换时，注意将```android:entries```和```android:entryValues```替换为```app:xxx```，如
```
<com.tplink.preference.ListPreferenceTP
          android:key="@string/key_str"
          android:title="@string/title_listpreference"
          android:dialogTitle="@string/dialog_title"
          android:defaultValue="@string/default_str"
          android:summary="@string/summary_str"
          app:entries="@array/entries_str"
          app:entryValues="@array/entries_values_str"/>
```
### 2.MultiSelectListPreferenceTP
新增MultiSelectListPreferenceTP，代码中直接替换MultiSelectListPreference即可，在xml替换时，注意将```android:entries```和```android:entryValues```替换为```app:xxx```，例子同ListPreference。

### 3.EditTextPreferenceTP
新增EditTextPreferenceTP，直接替换EditTextPreference即可。
<br>
<br>
<br>
## 其余一致性

### 1.滚动条一致性(含有ListView，RecyclerView等滚动属性的界面
在该界面主题中，添加如下属性：<br>
```
<item name="android:scrollbarThumbVertical">@drawable/scrollbar_handle_material_padding</item>
```

### 2.TabLayout的文字在英文下大小写
在TabLayout的布局中，加入如下属性:<br>
```
app:tabTextAppearance="@style/TabViewStyleTP"
```

### 3.溢出菜单自定义样式
增加了样式：@style/ActionModeTP,@style/SpinnerTP,@style/ContextPopupMenuTP分别用于不同类型的溢出菜单，应用替换即可。或者指定android:popupBackground属性为@drawable/spinner_background_roundrect_tp。
<br>
<br>
### 4. 标题栏图标一致性
在有标题栏的页面设置以下属性，用于统一标题栏返回键和溢出菜单键<br>
```
<item name="android:homeAsUpIndicator">@drawable/ic_ab_back_material</item>
<item name="android:actionModeCloseDrawable">@drawable/ic_ab_back_material</item>
<item name="android:actionOverflowButtonStyle">@style/ActionBarOverflowCloseDrawableStyleTP</item>
```
### 5.低内存字符串一致性
新增了低内存相关的字符串，供应用调用
```
<string name="tpwidgets_low_internal_storage_text_tp_1">存储空间不足，无法使用该功能</string>
<string name="tpwidgets_low_internal_storage_text_tp_2">存储空间不足，无法继续使用该功能</string>
```
<br>
