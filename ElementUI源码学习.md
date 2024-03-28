## Sass

Element-ui 的源码中使用到了很多高级的 Sass 语法

### !default

在读到 Element-ui 的 var.scss 文件的时候，看到定义了许多的变量，其中 !default 在多处使用

在Sass中，!default是一个特殊的声明，用于设置变量的默认值。当你在一个变量后面加上!default，这意味着如果这个变量在**当前作用域**或**父作用域**中没有被定义，那么它将被赋予!default后面指定的值。如果变量已经被定义了，那么!default将不会有任何效果，它不会覆盖已经存在的值。

这个特性在构建可复用的Sass库或框架时非常有用，因为它允许开发者提供一套默认的配置，同时允许用户在需要的时候覆盖这些默认值。

举个例子：


```css
// 定义一个变量，并给它一个默认值
$--color-primary: #409EFF !default;

// 在另一个地方，我们可以覆盖这个变量的值
$--color-primary: #123456;

// 使用变量
body {
  background-color: $--color-primary;
}
```


这种方式提供了一种安全的方式来设置变量的默认值，确保即使在用户忘记定义某个变量的情况下，样式也不会因为找不到变量而出错。

同时，也为前端开发者提供了足够的灵活性来自定义样式。

### Element-ui 定义的 Sass 变量

在不断的跳转定位的过程中，发现了 Element-ui 的定义变量的文件夹

在阅读其定义的变量时，可以将其分为两类

1. 基础属性变量的默认值设置
2. 组件属性变量的抽离

```css
/* Element Chalk Variables */

// Special comment for theme configurator
// type|skipAutoTranslation|Category|Order
// skipAutoTranslation 1

/* Transition
-------------------------- */
$--all-transition: all .3s cubic-bezier(.645,.045,.355,1) !default;
$--fade-transition: opacity 300ms cubic-bezier(0.23, 1, 0.32, 1) !default;
$--fade-linear-transition: opacity 200ms linear !default;
$--md-fade-transition: transform 300ms cubic-bezier(0.23, 1, 0.32, 1), opacity 300ms cubic-bezier(0.23, 1, 0.32, 1) !default;
$--border-transition-base: border-color .2s cubic-bezier(.645,.045,.355,1) !default;
$--color-transition-base: color .2s cubic-bezier(.645,.045,.355,1) !default;

/* Color
-------------------------- */
/// color|1|Brand Color|0
$--color-primary: #409EFF !default;
/// color|1|Background Color|4
$--color-white: #FFFFFF !default;
/// color|1|Background Color|4
$--color-black: #000000 !default;
$--color-primary-light-1: mix($--color-white, $--color-primary, 10%) !default; /* 53a8ff */
$--color-primary-light-2: mix($--color-white, $--color-primary, 20%) !default; /* 66b1ff */
$--color-primary-light-3: mix($--color-white, $--color-primary, 30%) !default; /* 79bbff */
$--color-primary-light-4: mix($--color-white, $--color-primary, 40%) !default; /* 8cc5ff */
$--color-primary-light-5: mix($--color-white, $--color-primary, 50%) !default; /* a0cfff */
$--color-primary-light-6: mix($--color-white, $--color-primary, 60%) !default; /* b3d8ff */
$--color-primary-light-7: mix($--color-white, $--color-primary, 70%) !default; /* c6e2ff */
$--color-primary-light-8: mix($--color-white, $--color-primary, 80%) !default; /* d9ecff */
$--color-primary-light-9: mix($--color-white, $--color-primary, 90%) !default; /* ecf5ff */
/// color|1|Functional Color|1
$--color-success: #67C23A !default;
/// color|1|Functional Color|1
$--color-warning: #E6A23C !default;
/// color|1|Functional Color|1
$--color-danger: #F56C6C !default;
/// color|1|Functional Color|1
$--color-info: #909399 !default;

$--color-success-light: mix($--color-white, $--color-success, 80%) !default;
$--color-warning-light: mix($--color-white, $--color-warning, 80%) !default;
$--color-danger-light: mix($--color-white, $--color-danger, 80%) !default;
$--color-info-light: mix($--color-white, $--color-info, 80%) !default;

$--color-success-lighter: mix($--color-white, $--color-success, 90%) !default;
$--color-warning-lighter: mix($--color-white, $--color-warning, 90%) !default;
$--color-danger-lighter: mix($--color-white, $--color-danger, 90%) !default;
$--color-info-lighter: mix($--color-white, $--color-info, 90%) !default;
/// color|1|Font Color|2
$--color-text-primary: #303133 !default;
/// color|1|Font Color|2
$--color-text-regular: #606266 !default;
/// color|1|Font Color|2
$--color-text-secondary: #909399 !default;
/// color|1|Font Color|2
$--color-text-placeholder: #C0C4CC !default;
/// color|1|Border Color|3
$--border-color-base: #DCDFE6 !default;
/// color|1|Border Color|3
$--border-color-light: #E4E7ED !default;
/// color|1|Border Color|3
$--border-color-lighter: #EBEEF5 !default;
/// color|1|Border Color|3
$--border-color-extra-light: #F2F6FC !default;

// Background
/// color|1|Background Color|4
$--background-color-base: #F5F7FA !default;

/* Link
-------------------------- */
$--link-color: $--color-primary-light-2 !default;
$--link-hover-color: $--color-primary !default;

/* Border
-------------------------- */
$--border-width-base: 1px !default;
$--border-style-base: solid !default;
$--border-color-hover: $--color-text-placeholder !default;
$--border-base: $--border-width-base $--border-style-base $--border-color-base !default;
/// borderRadius|1|Radius|0
$--border-radius-base: 4px !default;
/// borderRadius|1|Radius|0
$--border-radius-small: 2px !default;
/// borderRadius|1|Radius|0
$--border-radius-circle: 100% !default;
/// borderRadius|1|Radius|0
$--border-radius-zero: 0 !default;

// Box-shadow
/// boxShadow|1|Shadow|1
$--box-shadow-base: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04) !default;
// boxShadow|1|Shadow|1
$--box-shadow-dark: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .12) !default;
/// boxShadow|1|Shadow|1
$--box-shadow-light: 0 2px 12px 0 rgba(0, 0, 0, 0.1) !default;

/* Fill
-------------------------- */
$--fill-base: $--color-white !default;

/* Typography
-------------------------- */
$--font-path: 'fonts' !default;
$--font-display: 'auto' !default;
/// fontSize|1|Font Size|0
$--font-size-extra-large: 20px !default;
/// fontSize|1|Font Size|0
$--font-size-large: 18px !default;
/// fontSize|1|Font Size|0
$--font-size-medium: 16px !default;
/// fontSize|1|Font Size|0
$--font-size-base: 14px !default;
/// fontSize|1|Font Size|0
$--font-size-small: 13px !default;
/// fontSize|1|Font Size|0
$--font-size-extra-small: 12px !default;
/// fontWeight|1|Font Weight|1
$--font-weight-primary: 500 !default;
/// fontWeight|1|Font Weight|1
$--font-weight-secondary: 100 !default;
/// fontLineHeight|1|Line Height|2
$--font-line-height-primary: 24px !default;
/// fontLineHeight|1|Line Height|2
$--font-line-height-secondary: 16px !default;
$--font-color-disabled-base: #bbb !default;
/* Size
-------------------------- */
$--size-base: 14px !default;

/* z-index
-------------------------- */
$--index-normal: 1 !default;
$--index-top: 1000 !default;
$--index-popper: 2000 !default;

/* Disable base
-------------------------- */
$--disabled-fill-base: $--background-color-base !default;
$--disabled-color-base: $--color-text-placeholder !default;
$--disabled-border-base: $--border-color-light !default;

/* Icon
-------------------------- */
$--icon-color: #666 !default;
$--icon-color-base: $--color-info !default;

/* Checkbox
-------------------------- */
/// fontSize||Font|1
$--checkbox-font-size: 14px !default;
/// fontWeight||Font|1
$--checkbox-font-weight: $--font-weight-primary !default;
/// color||Color|0
$--checkbox-font-color: $--color-text-regular !default;
$--checkbox-input-height: 14px !default;
$--checkbox-input-width: 14px !default;
/// borderRadius||Border|2
$--checkbox-border-radius: $--border-radius-small !default;
/// color||Color|0
$--checkbox-background-color: $--color-white !default;
$--checkbox-input-border: $--border-base !default;

/// color||Color|0
$--checkbox-disabled-border-color: $--border-color-base !default;
$--checkbox-disabled-input-fill: #edf2fc !default;
$--checkbox-disabled-icon-color: $--color-text-placeholder !default;

$--checkbox-disabled-checked-input-fill: $--border-color-extra-light !default;
$--checkbox-disabled-checked-input-border-color: $--border-color-base !default;
$--checkbox-disabled-checked-icon-color: $--color-text-placeholder !default;

/// color||Color|0
$--checkbox-checked-font-color: $--color-primary !default;
$--checkbox-checked-input-border-color: $--color-primary !default;
/// color||Color|0
$--checkbox-checked-background-color: $--color-primary !default;
$--checkbox-checked-icon-color: $--fill-base !default;

$--checkbox-input-border-color-hover: $--color-primary !default;
/// height||Other|4
$--checkbox-bordered-height: 40px !default;
/// padding||Spacing|3
$--checkbox-bordered-padding: 9px 20px 9px 10px !default;
/// padding||Spacing|3
$--checkbox-bordered-medium-padding: 7px 20px 7px 10px !default;
/// padding||Spacing|3
$--checkbox-bordered-small-padding: 5px 15px 5px 10px !default;
/// padding||Spacing|3
$--checkbox-bordered-mini-padding: 3px 15px 3px 10px !default;
$--checkbox-bordered-medium-input-height: 14px !default;
$--checkbox-bordered-medium-input-width: 14px !default;
/// height||Other|4
$--checkbox-bordered-medium-height: 36px !default;
$--checkbox-bordered-small-input-height: 12px !default;
$--checkbox-bordered-small-input-width: 12px !default;
/// height||Other|4
$--checkbox-bordered-small-height: 32px !default;
$--checkbox-bordered-mini-input-height: 12px !default;
$--checkbox-bordered-mini-input-width: 12px !default;
/// height||Other|4
$--checkbox-bordered-mini-height: 28px !default;

/// color||Color|0
$--checkbox-button-checked-background-color: $--color-primary !default;
/// color||Color|0
$--checkbox-button-checked-font-color: $--color-white !default;
/// color||Color|0
$--checkbox-button-checked-border-color: $--color-primary !default;



/* Radio
-------------------------- */
/// fontSize||Font|1
$--radio-font-size: $--font-size-base !default;
/// fontWeight||Font|1
$--radio-font-weight: $--font-weight-primary !default;
/// color||Color|0
$--radio-font-color: $--color-text-regular !default;
$--radio-input-height: 14px !default;
$--radio-input-width: 14px !default;
/// borderRadius||Border|2
$--radio-input-border-radius: $--border-radius-circle !default;
/// color||Color|0
$--radio-input-background-color: $--color-white !default;
$--radio-input-border: $--border-base !default;
/// color||Color|0
$--radio-input-border-color: $--border-color-base !default;
/// color||Color|0
$--radio-icon-color: $--color-white !default;

$--radio-disabled-input-border-color: $--disabled-border-base !default;
$--radio-disabled-input-fill: $--disabled-fill-base !default;
$--radio-disabled-icon-color: $--disabled-fill-base !default;

$--radio-disabled-checked-input-border-color: $--disabled-border-base !default;
$--radio-disabled-checked-input-fill: $--disabled-fill-base !default;
$--radio-disabled-checked-icon-color: $--color-text-placeholder !default;

/// color||Color|0
$--radio-checked-font-color: $--color-primary !default;
/// color||Color|0
$--radio-checked-input-border-color: $--color-primary !default;
/// color||Color|0
$--radio-checked-input-background-color: $--color-white !default;
/// color||Color|0
$--radio-checked-icon-color: $--color-primary !default;

$--radio-input-border-color-hover: $--color-primary !default;

$--radio-bordered-height: 40px !default;
$--radio-bordered-padding: 12px 20px 0 10px !default;
$--radio-bordered-medium-padding: 10px 20px 0 10px !default;
$--radio-bordered-small-padding: 8px 15px 0 10px !default;
$--radio-bordered-mini-padding: 6px 15px 0 10px !default;
$--radio-bordered-medium-input-height: 14px !default;
$--radio-bordered-medium-input-width: 14px !default;
$--radio-bordered-medium-height: 36px !default;
$--radio-bordered-small-input-height: 12px !default;
$--radio-bordered-small-input-width: 12px !default;
$--radio-bordered-small-height: 32px !default;
$--radio-bordered-mini-input-height: 12px !default;
$--radio-bordered-mini-input-width: 12px !default;
$--radio-bordered-mini-height: 28px !default;

/// fontSize||Font|1
$--radio-button-font-size: $--font-size-base !default;
/// color||Color|0
$--radio-button-checked-background-color: $--color-primary !default;
/// color||Color|0
$--radio-button-checked-font-color: $--color-white !default;
/// color||Color|0
$--radio-button-checked-border-color: $--color-primary !default;
$--radio-button-disabled-checked-fill: $--border-color-extra-light !default;

/* Select
-------------------------- */
$--select-border-color-hover: $--border-color-hover !default;
$--select-disabled-border: $--disabled-border-base !default;
/// fontSize||Font|1
$--select-font-size: $--font-size-base !default;
$--select-close-hover-color: $--color-text-secondary !default;

$--select-input-color: $--color-text-placeholder !default;
$--select-multiple-input-color: #666 !default;
/// color||Color|0
$--select-input-focus-border-color: $--color-primary !default;
/// fontSize||Font|1
$--select-input-font-size: 14px !default;

$--select-option-color: $--color-text-regular !default;
$--select-option-disabled-color: $--color-text-placeholder !default;
$--select-option-disabled-background: $--color-white !default;
/// height||Other|4
$--select-option-height: 34px !default;
$--select-option-hover-background: $--background-color-base !default;
/// color||Color|0
$--select-option-selected-font-color: $--color-primary !default;
$--select-option-selected-hover: $--background-color-base !default;

$--select-group-color: $--color-info !default;
$--select-group-height: 30px !default;
$--select-group-font-size: 12px !default;

$--select-dropdown-background: $--color-white !default;
$--select-dropdown-shadow: $--box-shadow-light !default;
$--select-dropdown-empty-color: #999 !default;
/// height||Other|4
$--select-dropdown-max-height: 274px !default;
$--select-dropdown-padding: 6px 0 !default;
$--select-dropdown-empty-padding: 10px 0 !default;
$--select-dropdown-border: solid 1px $--border-color-light !default;

/* Alert
-------------------------- */
$--alert-padding: 8px 16px !default;
/// borderRadius||Border|2
$--alert-border-radius: $--border-radius-base !default;
/// fontSize||Font|1
$--alert-title-font-size: 13px !default;
/// fontSize||Font|1
$--alert-description-font-size: 12px !default;
/// fontSize||Font|1
$--alert-close-font-size: 12px !default;
/// fontSize||Font|1
$--alert-close-customed-font-size: 13px !default;

$--alert-success-color: $--color-success-lighter !default;
$--alert-info-color: $--color-info-lighter !default;
$--alert-warning-color: $--color-warning-lighter !default;
$--alert-danger-color: $--color-danger-lighter !default;

/// height||Other|4
$--alert-icon-size: 16px !default;
/// height||Other|4
$--alert-icon-large-size: 28px !default;

/* MessageBox
-------------------------- */
/// color||Color|0
$--messagebox-title-color: $--color-text-primary !default;
$--msgbox-width: 420px !default;
$--msgbox-border-radius: 4px !default;
/// fontSize||Font|1
$--messagebox-font-size: $--font-size-large !default;
/// fontSize||Font|1
$--messagebox-content-font-size: $--font-size-base !default;
/// color||Color|0
$--messagebox-content-color: $--color-text-regular !default;
/// fontSize||Font|1
$--messagebox-error-font-size: 12px !default;
$--msgbox-padding-primary: 15px !default;
/// color||Color|0
$--messagebox-success-color: $--color-success !default;
/// color||Color|0
$--messagebox-info-color: $--color-info !default;
/// color||Color|0
$--messagebox-warning-color: $--color-warning !default;
/// color||Color|0
$--messagebox-danger-color: $--color-danger !default;

/* Message
-------------------------- */
$--message-shadow: $--box-shadow-base !default;
$--message-min-width: 380px !default;
$--message-background-color: #edf2fc !default;
$--message-padding: 15px 15px 15px 20px !default;
/// color||Color|0
$--message-close-icon-color: $--color-text-placeholder !default;
/// height||Other|4
$--message-close-size: 16px !default;
/// color||Color|0
$--message-close-hover-color: $--color-text-secondary !default;

/// color||Color|0
$--message-success-font-color: $--color-success !default;
/// color||Color|0
$--message-info-font-color: $--color-info !default;
/// color||Color|0
$--message-warning-font-color: $--color-warning !default;
/// color||Color|0
$--message-danger-font-color: $--color-danger !default;

/* Notification
-------------------------- */
$--notification-width: 330px !default;
/// padding||Spacing|3
$--notification-padding: 14px 26px 14px 13px !default;
$--notification-radius: 8px !default;
$--notification-shadow: $--box-shadow-light !default;
/// color||Color|0
$--notification-border-color: $--border-color-lighter !default;
$--notification-icon-size: 24px !default;
$--notification-close-font-size: $--message-close-size !default;
$--notification-group-margin-left: 13px !default;
$--notification-group-margin-right: 8px !default;
/// fontSize||Font|1
$--notification-content-font-size: $--font-size-base !default;
/// color||Color|0
$--notification-content-color: $--color-text-regular !default;
/// fontSize||Font|1
$--notification-title-font-size: 16px !default;
/// color||Color|0
$--notification-title-color: $--color-text-primary !default;

/// color||Color|0
$--notification-close-color: $--color-text-secondary !default;
/// color||Color|0
$--notification-close-hover-color: $--color-text-regular !default;

/// color||Color|0
$--notification-success-icon-color: $--color-success !default;
/// color||Color|0
$--notification-info-icon-color: $--color-info !default;
/// color||Color|0
$--notification-warning-icon-color: $--color-warning !default;
/// color||Color|0
$--notification-danger-icon-color: $--color-danger !default;

/* Input
-------------------------- */
$--input-font-size: $--font-size-base !default;
/// color||Color|0
$--input-font-color: $--color-text-regular !default;
/// height||Other|4
$--input-height: 40px !default;
$--input-border: $--border-base !default;
$--input-border-color: $--border-color-base !default;
/// borderRadius||Border|2
$--input-border-radius: $--border-radius-base !default;
$--input-border-color-hover: $--border-color-hover !default;
/// color||Color|0
$--input-background-color: $--color-white !default;
$--input-fill-disabled: $--disabled-fill-base !default;
$--input-color-disabled: $--font-color-disabled-base !default;
/// color||Color|0
$--input-icon-color: $--color-text-placeholder !default;
/// color||Color|0
$--input-placeholder-color: $--color-text-placeholder !default;
$--input-max-width: 314px !default;

$--input-hover-border: $--border-color-hover !default;
$--input-clear-hover-color: $--color-text-secondary !default;

$--input-focus-border: $--color-primary !default;
$--input-focus-fill: $--color-white !default;

$--input-disabled-fill: $--disabled-fill-base !default;
$--input-disabled-border: $--disabled-border-base !default;
$--input-disabled-color: $--disabled-color-base !default;
$--input-disabled-placeholder-color: $--color-text-placeholder !default;

/// fontSize||Font|1
$--input-medium-font-size: 14px !default;
/// height||Other|4
$--input-medium-height: 36px !default;
/// fontSize||Font|1
$--input-small-font-size: 13px !default;
/// height||Other|4
$--input-small-height: 32px !default;
/// fontSize||Font|1
$--input-mini-font-size: 12px !default;
/// height||Other|4
$--input-mini-height: 28px !default;

/* Cascader
-------------------------- */
/// color||Color|0
$--cascader-menu-font-color: $--color-text-regular !default;
/// color||Color|0
$--cascader-menu-selected-font-color: $--color-primary !default;
$--cascader-menu-fill: $--fill-base !default;
$--cascader-menu-font-size: $--font-size-base !default;
$--cascader-menu-radius: $--border-radius-base !default;
$--cascader-menu-border: solid 1px $--border-color-light !default;
$--cascader-menu-shadow: $--box-shadow-light !default;
$--cascader-node-background-hover: $--background-color-base !default;
$--cascader-node-color-disabled:$--color-text-placeholder !default;
$--cascader-color-empty:$--color-text-placeholder !default;
$--cascader-tag-background: #f0f2f5;

/* Group
-------------------------- */
$--group-option-flex: 0 0 (1/5) * 100% !default;
$--group-option-offset-bottom: 12px !default;
$--group-option-fill-hover: rgba($--color-black, 0.06) !default;
$--group-title-color: $--color-black !default;
$--group-title-font-size: $--font-size-base !default;
$--group-title-width: 66px !default;

/* Tab
-------------------------- */
$--tab-font-size: $--font-size-base !default;
$--tab-border-line: 1px solid #e4e4e4 !default;
$--tab-header-color-active: $--color-text-secondary !default;
$--tab-header-color-hover: $--color-text-regular !default;
$--tab-header-color: $--color-text-regular !default;
$--tab-header-fill-active: rgba($--color-black, 0.06) !default;
$--tab-header-fill-hover: rgba($--color-black, 0.06) !default;
$--tab-vertical-header-width: 90px !default;
$--tab-vertical-header-count-color: $--color-white !default;
$--tab-vertical-header-count-fill: $--color-text-secondary !default;

/* Button
-------------------------- */
/// fontSize||Font|1
$--button-font-size: $--font-size-base !default;
/// fontWeight||Font|1
$--button-font-weight: $--font-weight-primary !default;
/// borderRadius||Border|2
$--button-border-radius: $--border-radius-base !default;
/// padding||Spacing|3
$--button-padding-vertical: 12px !default;
/// padding||Spacing|3
$--button-padding-horizontal: 20px !default;

/// fontSize||Font|1
$--button-medium-font-size: $--font-size-base !default;
/// borderRadius||Border|2
$--button-medium-border-radius: $--border-radius-base !default;
/// padding||Spacing|3
$--button-medium-padding-vertical: 10px !default;
/// padding||Spacing|3
$--button-medium-padding-horizontal: 20px !default;

/// fontSize||Font|1
$--button-small-font-size: 12px !default;
$--button-small-border-radius: #{$--border-radius-base - 1} !default;
/// padding||Spacing|3
$--button-small-padding-vertical: 9px !default;
/// padding||Spacing|3
$--button-small-padding-horizontal: 15px !default;
/// fontSize||Font|1
$--button-mini-font-size: 12px !default;
$--button-mini-border-radius: #{$--border-radius-base - 1} !default;
/// padding||Spacing|3
$--button-mini-padding-vertical: 7px !default;
/// padding||Spacing|3
$--button-mini-padding-horizontal: 15px !default;

/// color||Color|0
$--button-default-font-color: $--color-text-regular !default;
/// color||Color|0
$--button-default-background-color: $--color-white !default;
/// color||Color|0
$--button-default-border-color: $--border-color-base !default;

/// color||Color|0
$--button-disabled-font-color: $--color-text-placeholder !default;
/// color||Color|0
$--button-disabled-background-color: $--color-white !default;
/// color||Color|0
$--button-disabled-border-color: $--border-color-lighter !default;

/// color||Color|0
$--button-primary-border-color: $--color-primary !default;
/// color||Color|0
$--button-primary-font-color: $--color-white !default;
/// color||Color|0
$--button-primary-background-color: $--color-primary !default;
/// color||Color|0
$--button-success-border-color: $--color-success !default;
/// color||Color|0
$--button-success-font-color: $--color-white !default;
/// color||Color|0
$--button-success-background-color: $--color-success !default;
/// color||Color|0
$--button-warning-border-color: $--color-warning !default;
/// color||Color|0
$--button-warning-font-color: $--color-white !default;
/// color||Color|0
$--button-warning-background-color: $--color-warning !default;
/// color||Color|0
$--button-danger-border-color: $--color-danger !default;
/// color||Color|0
$--button-danger-font-color: $--color-white !default;
/// color||Color|0
$--button-danger-background-color: $--color-danger !default;
/// color||Color|0
$--button-info-border-color: $--color-info !default;
/// color||Color|0
$--button-info-font-color: $--color-white !default;
/// color||Color|0
$--button-info-background-color: $--color-info !default;

$--button-hover-tint-percent: 20% !default;
$--button-active-shade-percent: 10% !default;


/* cascader
-------------------------- */
$--cascader-height: 200px !default;

/* Switch
-------------------------- */
/// color||Color|0
$--switch-on-color: $--color-primary !default;
/// color||Color|0
$--switch-off-color: $--border-color-base !default;
/// fontSize||Font|1
$--switch-font-size: $--font-size-base !default;
$--switch-core-border-radius: 10px !default;
// height||Other|4 TODO: width 代码写死的40px 所以下面这三个属性都没意义
$--switch-width: 40px !default;
// height||Other|4
$--switch-height: 20px !default;
// height||Other|4
$--switch-button-size: 16px !default;

/* Dialog
-------------------------- */
$--dialog-background-color: $--color-white !default;
$--dialog-box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3) !default;
/// fontSize||Font|1
$--dialog-title-font-size: $--font-size-large !default;
/// fontSize||Font|1
$--dialog-content-font-size: 14px !default;
/// fontLineHeight||LineHeight|2
$--dialog-font-line-height: $--font-line-height-primary !default;
/// padding||Spacing|3
$--dialog-padding-primary: 20px !default;

/* Table
-------------------------- */
/// color||Color|0
$--table-border-color: $--border-color-lighter !default;
$--table-border: 1px solid $--table-border-color !default;
/// color||Color|0
$--table-font-color: $--color-text-regular !default;
/// color||Color|0
$--table-header-font-color: $--color-text-secondary !default;
/// color||Color|0
$--table-row-hover-background-color: $--background-color-base !default;
$--table-current-row-background-color: $--color-primary-light-9 !default;
/// color||Color|0
$--table-header-background-color: $--color-white !default;
$--table-fixed-box-shadow: 0 0 10px rgba(0, 0, 0, .12) !default;

/* Pagination
-------------------------- */
/// fontSize||Font|1
$--pagination-font-size: 13px !default;
/// color||Color|0
$--pagination-background-color: $--color-white !default;
/// color||Color|0
$--pagination-font-color: $--color-text-primary !default;
$--pagination-border-radius: 3px !default;
/// color||Color|0
$--pagination-button-color: $--color-text-primary !default;
/// height||Other|4
$--pagination-button-width: 35.5px !default;
/// height||Other|4
$--pagination-button-height: 28px !default;
/// color||Color|0
$--pagination-button-disabled-color: $--color-text-placeholder !default;
/// color||Color|0
$--pagination-button-disabled-background-color: $--color-white !default;
/// color||Color|0
$--pagination-hover-color: $--color-primary !default;

/* Popup
-------------------------- */
/// color||Color|0
$--popup-modal-background-color: $--color-black !default;
/// opacity||Other|1
$--popup-modal-opacity: 0.5 !default;

/* Popover
-------------------------- */
/// color||Color|0
$--popover-background-color: $--color-white !default;
/// fontSize||Font|1
$--popover-font-size: $--font-size-base !default;
/// color||Color|0
$--popover-border-color: $--border-color-lighter !default;
$--popover-arrow-size: 6px !default;
/// padding||Spacing|3
$--popover-padding: 12px !default;
$--popover-padding-large: 18px 20px !default;
/// fontSize||Font|1
$--popover-title-font-size: 16px !default;
/// color||Color|0
$--popover-title-font-color: $--color-text-primary !default;

/* Tooltip
-------------------------- */
/// color|1|Color|0
$--tooltip-fill: $--color-text-primary !default;
/// color|1|Color|0
$--tooltip-color: $--color-white !default;
/// fontSize||Font|1
$--tooltip-font-size: 12px !default;
/// color||Color|0
$--tooltip-border-color: $--color-text-primary !default;
$--tooltip-arrow-size: 6px !default;
/// padding||Spacing|3
$--tooltip-padding: 10px !default;

/* Tag
-------------------------- */
/// color||Color|0
$--tag-info-color: $--color-info !default;
/// color||Color|0
$--tag-primary-color: $--color-primary !default;
/// color||Color|0
$--tag-success-color: $--color-success !default;
/// color||Color|0
$--tag-warning-color: $--color-warning !default;
/// color||Color|0
$--tag-danger-color: $--color-danger !default;
/// fontSize||Font|1
$--tag-font-size: 12px !default;
$--tag-border-radius: 4px !default;
$--tag-padding: 0 10px !default;

/* Tree
-------------------------- */
/// color||Color|0
$--tree-node-hover-background-color: $--background-color-base !default;
/// color||Color|0
$--tree-font-color: $--color-text-regular !default;
/// color||Color|0
$--tree-expand-icon-color: $--color-text-placeholder !default;

/* Dropdown
-------------------------- */
$--dropdown-menu-box-shadow: $--box-shadow-light !default;
$--dropdown-menuItem-hover-fill: $--color-primary-light-9 !default;
$--dropdown-menuItem-hover-color: $--link-color !default;

/* Badge
-------------------------- */
/// color||Color|0
$--badge-background-color: $--color-danger !default;
$--badge-radius: 10px !default;
/// fontSize||Font|1
$--badge-font-size: 12px !default;
/// padding||Spacing|3
$--badge-padding: 6px !default;
/// height||Other|4
$--badge-size: 18px !default;

/* Card
--------------------------*/
/// color||Color|0
$--card-border-color: $--border-color-lighter !default;
$--card-border-radius: 4px !default;
/// padding||Spacing|3
$--card-padding: 20px !default;

/* Slider
--------------------------*/
/// color||Color|0
$--slider-main-background-color: $--color-primary !default;
/// color||Color|0
$--slider-runway-background-color: $--border-color-light !default;
$--slider-button-hover-color: mix($--color-primary, black, 97%) !default;
$--slider-stop-background-color: $--color-white !default;
$--slider-disable-color: $--color-text-placeholder !default;
$--slider-margin: 16px 0 !default;
$--slider-border-radius: 3px !default;
/// height|1|Other|4
$--slider-height: 6px !default;
/// height||Other|4
$--slider-button-size: 16px !default;
$--slider-button-wrapper-size: 36px !default;
$--slider-button-wrapper-offset: -15px !default;

/* Steps
--------------------------*/
$--steps-border-color: $--disabled-border-base !default;
$--steps-border-radius: 4px !default;
$--steps-padding: 20px !default;

/* Menu
--------------------------*/
/// fontSize||Font|1
$--menu-item-font-size: $--font-size-base !default;
/// color||Color|0
$--menu-item-font-color: $--color-text-primary !default;
/// color||Color|0
$--menu-background-color: $--color-white !default;
$--menu-item-hover-fill: $--color-primary-light-9 !default;

/* Rate
--------------------------*/
$--rate-height: 20px !default;
/// fontSize||Font|1
$--rate-font-size: $--font-size-base !default;
/// height||Other|3
$--rate-icon-size: 18px !default;
/// margin||Spacing|2
$--rate-icon-margin: 6px !default;
$--rate-icon-color: $--color-text-placeholder !default;

/* DatePicker
--------------------------*/
$--datepicker-font-color: $--color-text-regular !default;
/// color|1|Color|0
$--datepicker-off-font-color: $--color-text-placeholder !default;
/// color||Color|0
$--datepicker-header-font-color: $--color-text-regular !default;
$--datepicker-icon-color: $--color-text-primary !default;
$--datepicker-border-color: $--disabled-border-base !default;
$--datepicker-inner-border-color: #e4e4e4 !default;
/// color||Color|0
$--datepicker-inrange-background-color: $--border-color-extra-light !default;
/// color||Color|0
$--datepicker-inrange-hover-background-color: $--border-color-extra-light !default;
/// color||Color|0
$--datepicker-active-color: $--color-primary !default;
/// color||Color|0
$--datepicker-hover-font-color: $--color-primary !default;
$--datepicker-cell-hover-color: #fff !default;

/* Loading
--------------------------*/
/// height||Other|4
$--loading-spinner-size: 42px !default;
/// height||Other|4
$--loading-fullscreen-spinner-size: 50px !default;

/* Scrollbar
--------------------------*/
$--scrollbar-background-color: rgba($--color-text-secondary, .3) !default;
$--scrollbar-hover-background-color: rgba($--color-text-secondary, .5) !default;

/* Carousel
--------------------------*/
/// fontSize||Font|1
$--carousel-arrow-font-size: 12px !default;
$--carousel-arrow-size: 36px !default;
$--carousel-arrow-background: rgba(31, 45, 61, 0.11) !default;
$--carousel-arrow-hover-background: rgba(31, 45, 61, 0.23) !default;
/// width||Other|4
$--carousel-indicator-width: 30px !default;
/// height||Other|4
$--carousel-indicator-height: 2px !default;
$--carousel-indicator-padding-horizontal: 4px !default;
$--carousel-indicator-padding-vertical: 12px !default;
$--carousel-indicator-out-color: $--border-color-hover !default;

/* Collapse
--------------------------*/
/// color||Color|0
$--collapse-border-color: $--border-color-lighter !default;
/// height||Other|4
$--collapse-header-height: 48px !default;
/// color||Color|0
$--collapse-header-background-color: $--color-white !default;
/// color||Color|0
$--collapse-header-font-color: $--color-text-primary !default;
/// fontSize||Font|1
$--collapse-header-font-size: 13px !default;
/// color||Color|0
$--collapse-content-background-color: $--color-white !default;
/// fontSize||Font|1
$--collapse-content-font-size: 13px !default;
/// color||Color|0
$--collapse-content-font-color: $--color-text-primary !default;

/* Transfer
--------------------------*/
$--transfer-border-color: $--border-color-lighter !default;
$--transfer-border-radius: $--border-radius-base !default;
/// height||Other|4
$--transfer-panel-width: 200px !default;
/// height||Other|4
$--transfer-panel-header-height: 40px !default;
/// color||Color|0
$--transfer-panel-header-background-color: $--background-color-base !default;
/// height||Other|4
$--transfer-panel-footer-height: 40px !default;
/// height||Other|4
$--transfer-panel-body-height: 246px !default;
/// height||Other|4
$--transfer-item-height: 30px !default;
/// height||Other|4
$--transfer-filter-height: 32px !default;

/* Header
  --------------------------*/
$--header-padding: 0 20px !default;

/* Footer
--------------------------*/
$--footer-padding: 0 20px !default;

/* Main
--------------------------*/
$--main-padding: 20px !default;

/* Timeline
--------------------------*/
$--timeline-node-size-normal: 12px !default;
$--timeline-node-size-large: 14px !default;
$--timeline-node-color: $--border-color-light !default;

/* Backtop
--------------------------*/
/// color||Color|0
$--backtop-background-color: $--color-white !default;
/// color||Color|0
$--backtop-font-color: $--color-primary !default;
/// color||Color|0
$--backtop-hover-background-color: $--border-color-extra-light !default;

/* Link
--------------------------*/
/// fontSize||Font|1
$--link-font-size: $--font-size-base !default;
/// fontWeight||Font|1
$--link-font-weight: $--font-weight-primary !default;
/// color||Color|0
$--link-default-font-color: $--color-text-regular !default;
/// color||Color|0
$--link-default-active-color: $--color-primary !default;
/// color||Color|0
$--link-disabled-font-color: $--color-text-placeholder !default;
/// color||Color|0
$--link-primary-font-color: $--color-primary !default;
/// color||Color|0
$--link-success-font-color: $--color-success !default;
/// color||Color|0
$--link-warning-font-color: $--color-warning !default;
/// color||Color|0
$--link-danger-font-color: $--color-danger !default;
/// color||Color|0
$--link-info-font-color: $--color-info !default;
/* Calendar
--------------------------*/
/// border||Other|4
$--calendar-border: $--table-border !default;
/// color||Other|4
$--calendar-selected-background-color: #F2F8FE !default;
$--calendar-cell-width: 85px !default;

/* Form
-------------------------- */
/// fontSize||Font|1
$--form-label-font-size: $--font-size-base !default;

/* Avatar
--------------------------*/
/// color||Color|0
$--avatar-font-color: #fff !default;
/// color||Color|0
$--avatar-background-color: #C0C4CC !default;
/// fontSize||Font Size|1
$--avatar-text-font-size: 14px !default;
/// fontSize||Font Size|1
$--avatar-icon-font-size: 18px !default;
/// borderRadius||Border|2
$--avatar-border-radius: $--border-radius-base !default;
/// size|1|Avatar Size|3
$--avatar-large-size: 40px !default;
/// size|1|Avatar Size|3
$--avatar-medium-size: 36px !default;
/// size|1|Avatar Size|3
$--avatar-small-size: 28px !default;

/* Empty
-------------------------- */
$--empty-padding: 40px 0 !default;
$--empty-image-width: 160px !default;
$--empty-description-margin-top: 20px !default;
$--empty-bottom-margin-top: 20px !default;

/* Descriptions
-------------------------- */
$--descriptions-header-margin-bottom: 20px !default;
$--descriptions-title-font-size: 16px !default;
$--descriptions-table-border: 1px solid $--border-color-lighter !default;
$--descriptions-item-bordered-label-background: #fafafa !default;

/* Skeleton 
--------------------------*/
$--skeleton-color: #f2f2f2 !default;
$--skeleton-to-color: #e6e6e6 !default;

/* Svg
--------------- */
$--svg-monochrome-grey: #DCDDE0 !default;

/* Result
-------------------------- */
$--result-padding: 40px 30px !default;
$--result-icon-font-size: 64px !default;
$--result-title-font-size: 20px !default;
$--result-title-margin-top: 20px !default;
$--result-subtitle-margin-top: 10px !default;
$--result-extra-margin-top: 30px !default;
$--result-info-color: $--color-info !default;
$--result-success-color: $--color-success !default;
$--result-warning-color: $--color-warning !default;
$--result-danger-color: $--color-danger !default;

/* Break-point
--------------------------*/
$--sm: 768px !default;
$--md: 992px !default;
$--lg: 1200px !default;
$--xl: 1920px !default;

$--breakpoints: (
  'xs' : (max-width: $--sm - 1),
  'sm' : (min-width: $--sm),
  'md' : (min-width: $--md),
  'lg' : (min-width: $--lg),
  'xl' : (min-width: $--xl)
);

$--breakpoints-spec: (
  'xs-only' : (max-width: $--sm - 1),
  'sm-and-up' : (min-width: $--sm),
  'sm-only': "(min-width: #{$--sm}) and (max-width: #{$--md - 1})",
  'sm-and-down': (max-width: $--md - 1),
  'md-and-up' : (min-width: $--md),
  'md-only': "(min-width: #{$--md}) and (max-width: #{$--lg - 1})",
  'md-and-down': (max-width: $--lg - 1),
  'lg-and-up' : (min-width: $--lg),
  'lg-only': "(min-width: #{$--lg}) and (max-width: #{$--xl - 1})",
  'lg-and-down': (max-width: $--xl - 1),
  'xl-only' : (min-width: $--xl),
);
```

### icon.scss

继续跳转文件，看到了 icon.scss

这里用来定义了 Element-ui 的基础图标

这里需要重点读懂这里的两段代码

一、

```css
@font-face {
  font-family: 'element-icons';
  src: url('#{$--font-path}/element-icons.woff') format('woff'), /* chrome, firefox */
       url('#{$--font-path}/element-icons.ttf') format('truetype'); /* chrome, firefox, opera, Safari, Android, iOS 4.2+*/
  font-weight: normal;
  font-display: $--font-display;
  font-style: normal;
}
```

1. @font-face 是CSS中的一个规则，用来定义网页中使用的字体。通过这个规则，就可以引入在线字体或者本地字体文件，让网页显示特殊的字体样式。

2. font-family: 'element-icons'; 这一行设置了字体的名称，这里命名为element-icons。当你在CSS中引用这个字体时，就会使用这个名称。

3. src: url('#{$--font-path}/element-icons.woff') format('woff'), 这里指定了字体文件的路径和格式。url函数用于引入字体文件，#{$--font-path}是一个变量，它包含了字体文件存放的路径。element-icons.woff是字体文件的名称，**woff是它的格式**，这种格式的字体文件在多数现代浏览器中都有很好的支持。

4. format('truetype') 这一部分是注释，说明接下来的字体格式是truetype，这种格式的字体文件在多个浏览器和操作系统中都得到了支持。

5. url('#{$--font-path}/element-icons.ttf') format('truetype'); 这一行同样使用url函数引入了另一种格式的字体文件，element-icons.ttf。truetype是ttf字体文件的格式，它同样被广泛支持。

6. font-weight: normal; 这里设置了字体的粗细程度，normal表示正常粗细，这是字体的默认设置。

7. font-display: $--font-display; 这一行通过变量$--font-display来控制字体文件如何被加载和显示。这个变量的值可以是auto、block或fallback，用来优化字体加载的性能和用户体验。

8. font-style: normal; 最后这一行设置了字体的风格，normal表示正常风格，没有斜体或粗体效果。

二、

```css
[class^="el-icon-"], [class*=" el-icon-"] {
  /* use !important to prevent issues with browser extensions that change fonts */
  font-family: 'element-icons' !important;
  speak: none;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  line-height: 1;
  vertical-align: baseline;
  display: inline-block;

  /* Better Font Rendering =========== */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

1. 选择器 `[class^="el-icon-"]` 和 `[class*=" el-icon-"]` 用于选择那些class属性值以 "el-icon-" 开头或包含 " el-icon-" 的HTML元素。

例如这个就被匹配到了：

这个字体图标会应用上如上的字体属性。这里只需要改变 `content` 就可以了。

```css
.el-icon-ice-cream-round:before {
  content: "\e6a0";
}
```

2. font-family: 'element-icons' !important; 这一行强制定义了这些被选中的元素应该使用的字体家族，这里是 'element-icons'。使用 !important 是为了保证这个样式规则的优先级高于其他可能冲突的样式规则。

3. speak: none; 告诉浏览器不要为这些图标元素发声读出，因为它们是视觉图标，不需要被读出。

4. font-style: normal; 和 font-weight: normal; 这两行确保了图标的字体样式和粗细都是标准的，没有斜体或加粗效果。

5. font-variant: normal; 这一行保持了字体的小写字母不变，不进行任何特殊的字体变化。

6. text-transform: none; 这一行确保文本不会被转换成大写或小写，保持原有样式。

7. line-height: 1; 这一行设置了行高为1，意味着图标的高度就是它的字体大小，这样可以确保图标不会占据额外的垂直空间。

8. vertical-align: baseline; 这一行将图标垂直对齐到基线，这样图标就会和周围的文本元素对齐得很好。

9. display: inline-block; 这一行让图标表现得像一个内联元素，但它也可以拥有块级元素的属性，比如宽度和高度。

10. -webkit-font-smoothing: antialiased; 和 -moz-osx-font-smoothing: grayscale; 这两行是为了在不同的浏览器和操作系统上提供更平滑的字体渲染效果，使得图标看起来更加清晰。


完整代码如下：

```css
@import "common/var"; // 引入变量

@font-face {
  font-family: 'element-icons';
  src: url('#{$--font-path}/element-icons.woff') format('woff'), /* chrome, firefox */
       url('#{$--font-path}/element-icons.ttf') format('truetype'); /* chrome, firefox, opera, Safari, Android, iOS 4.2+*/
  font-weight: normal;
  font-display: $--font-display;
  font-style: normal;
}

[class^="el-icon-"], [class*=" el-icon-"] {
  /* use !important to prevent issues with browser extensions that change fonts */
  font-family: 'element-icons' !important;
  speak: none;
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  text-transform: none;
  line-height: 1;
  vertical-align: baseline;
  display: inline-block;

  /* Better Font Rendering =========== */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.el-icon-ice-cream-round:before {
  content: "\e6a0";
}

.el-icon-ice-cream-square:before {
  content: "\e6a3";
}

.el-icon-lollipop:before {
  content: "\e6a4";
}

.el-icon-potato-strips:before {
  content: "\e6a5";
}

.el-icon-milk-tea:before {
  content: "\e6a6";
}

.el-icon-ice-drink:before {
  content: "\e6a7";
}

.el-icon-ice-tea:before {
  content: "\e6a9";
}

.el-icon-coffee:before {
  content: "\e6aa";
}

.el-icon-orange:before {
  content: "\e6ab";
}

.el-icon-pear:before {
  content: "\e6ac";
}

.el-icon-apple:before {
  content: "\e6ad";
}

.el-icon-cherry:before {
  content: "\e6ae";
}

.el-icon-watermelon:before {
  content: "\e6af";
}

.el-icon-grape:before {
  content: "\e6b0";
}

.el-icon-refrigerator:before {
  content: "\e6b1";
}

.el-icon-goblet-square-full:before {
  content: "\e6b2";
}

.el-icon-goblet-square:before {
  content: "\e6b3";
}

.el-icon-goblet-full:before {
  content: "\e6b4";
}

.el-icon-goblet:before {
  content: "\e6b5";
}

.el-icon-cold-drink:before {
  content: "\e6b6";
}

.el-icon-coffee-cup:before {
  content: "\e6b8";
}

.el-icon-water-cup:before {
  content: "\e6b9";
}

.el-icon-hot-water:before {
  content: "\e6ba";
}

.el-icon-ice-cream:before {
  content: "\e6bb";
}

.el-icon-dessert:before {
  content: "\e6bc";
}

.el-icon-sugar:before {
  content: "\e6bd";
}

.el-icon-tableware:before {
  content: "\e6be";
}

.el-icon-burger:before {
  content: "\e6bf";
}

.el-icon-knife-fork:before {
  content: "\e6c1";
}

.el-icon-fork-spoon:before {
  content: "\e6c2";
}

.el-icon-chicken:before {
  content: "\e6c3";
}

.el-icon-food:before {
  content: "\e6c4";
}

.el-icon-dish-1:before {
  content: "\e6c5";
}

.el-icon-dish:before {
  content: "\e6c6";
}

.el-icon-moon-night:before {
  content: "\e6ee";
}

.el-icon-moon:before {
  content: "\e6f0";
}

.el-icon-cloudy-and-sunny:before {
  content: "\e6f1";
}

.el-icon-partly-cloudy:before {
  content: "\e6f2";
}

.el-icon-cloudy:before {
  content: "\e6f3";
}

.el-icon-sunny:before {
  content: "\e6f6";
}

.el-icon-sunset:before {
  content: "\e6f7";
}

.el-icon-sunrise-1:before {
  content: "\e6f8";
}

.el-icon-sunrise:before {
  content: "\e6f9";
}

.el-icon-heavy-rain:before {
  content: "\e6fa";
}

.el-icon-lightning:before {
  content: "\e6fb";
}

.el-icon-light-rain:before {
  content: "\e6fc";
}

.el-icon-wind-power:before {
  content: "\e6fd";
}

.el-icon-baseball:before {
  content: "\e712";
}

.el-icon-soccer:before {
  content: "\e713";
}

.el-icon-football:before {
  content: "\e715";
}

.el-icon-basketball:before {
  content: "\e716";
}

.el-icon-ship:before {
  content: "\e73f";
}

.el-icon-truck:before {
  content: "\e740";
}

.el-icon-bicycle:before {
  content: "\e741";
}

.el-icon-mobile-phone:before {
  content: "\e6d3";
}

.el-icon-service:before {
  content: "\e6d4";
}

.el-icon-key:before {
  content: "\e6e2";
}

.el-icon-unlock:before {
  content: "\e6e4";
}

.el-icon-lock:before {
  content: "\e6e5";
}

.el-icon-watch:before {
  content: "\e6fe";
}

.el-icon-watch-1:before {
  content: "\e6ff";
}

.el-icon-timer:before {
  content: "\e702";
}

.el-icon-alarm-clock:before {
  content: "\e703";
}

.el-icon-map-location:before {
  content: "\e704";
}

.el-icon-delete-location:before {
  content: "\e705";
}

.el-icon-add-location:before {
  content: "\e706";
}

.el-icon-location-information:before {
  content: "\e707";
}

.el-icon-location-outline:before {
  content: "\e708";
}

.el-icon-location:before {
  content: "\e79e";
}

.el-icon-place:before {
  content: "\e709";
}

.el-icon-discover:before {
  content: "\e70a";
}

.el-icon-first-aid-kit:before {
  content: "\e70b";
}

.el-icon-trophy-1:before {
  content: "\e70c";
}

.el-icon-trophy:before {
  content: "\e70d";
}

.el-icon-medal:before {
  content: "\e70e";
}

.el-icon-medal-1:before {
  content: "\e70f";
}

.el-icon-stopwatch:before {
  content: "\e710";
}

.el-icon-mic:before {
  content: "\e711";
}

.el-icon-copy-document:before {
  content: "\e718";
}

.el-icon-full-screen:before {
  content: "\e719";
}

.el-icon-switch-button:before {
  content: "\e71b";
}

.el-icon-aim:before {
  content: "\e71c";
}

.el-icon-crop:before {
  content: "\e71d";
}

.el-icon-odometer:before {
  content: "\e71e";
}

.el-icon-time:before {
  content: "\e71f";
}

.el-icon-bangzhu:before {
  content: "\e724";
}

.el-icon-close-notification:before {
  content: "\e726";
}

.el-icon-microphone:before {
  content: "\e727";
}

.el-icon-turn-off-microphone:before {
  content: "\e728";
}

.el-icon-position:before {
  content: "\e729";
}

.el-icon-postcard:before {
  content: "\e72a";
}

.el-icon-message:before {
  content: "\e72b";
}

.el-icon-chat-line-square:before {
  content: "\e72d";
}

.el-icon-chat-dot-square:before {
  content: "\e72e";
}

.el-icon-chat-dot-round:before {
  content: "\e72f";
}

.el-icon-chat-square:before {
  content: "\e730";
}

.el-icon-chat-line-round:before {
  content: "\e731";
}

.el-icon-chat-round:before {
  content: "\e732";
}

.el-icon-set-up:before {
  content: "\e733";
}

.el-icon-turn-off:before {
  content: "\e734";
}

.el-icon-open:before {
  content: "\e735";
}

.el-icon-connection:before {
  content: "\e736";
}

.el-icon-link:before {
  content: "\e737";
}

.el-icon-cpu:before {
  content: "\e738";
}

.el-icon-thumb:before {
  content: "\e739";
}

.el-icon-female:before {
  content: "\e73a";
}

.el-icon-male:before {
  content: "\e73b";
}

.el-icon-guide:before {
  content: "\e73c";
}

.el-icon-news:before {
  content: "\e73e";
}

.el-icon-price-tag:before {
  content: "\e744";
}

.el-icon-discount:before {
  content: "\e745";
}

.el-icon-wallet:before {
  content: "\e747";
}

.el-icon-coin:before {
  content: "\e748";
}

.el-icon-money:before {
  content: "\e749";
}

.el-icon-bank-card:before {
  content: "\e74a";
}

.el-icon-box:before {
  content: "\e74b";
}

.el-icon-present:before {
  content: "\e74c";
}

.el-icon-sell:before {
  content: "\e6d5";
}

.el-icon-sold-out:before {
  content: "\e6d6";
}

.el-icon-shopping-bag-2:before {
  content: "\e74d";
}

.el-icon-shopping-bag-1:before {
  content: "\e74e";
}

.el-icon-shopping-cart-2:before {
  content: "\e74f";
}

.el-icon-shopping-cart-1:before {
  content: "\e750";
}

.el-icon-shopping-cart-full:before {
  content: "\e751";
}

.el-icon-smoking:before {
  content: "\e752";
}

.el-icon-no-smoking:before {
  content: "\e753";
}

.el-icon-house:before {
  content: "\e754";
}

.el-icon-table-lamp:before {
  content: "\e755";
}

.el-icon-school:before {
  content: "\e756";
}

.el-icon-office-building:before {
  content: "\e757";
}

.el-icon-toilet-paper:before {
  content: "\e758";
}

.el-icon-notebook-2:before {
  content: "\e759";
}

.el-icon-notebook-1:before {
  content: "\e75a";
}

.el-icon-files:before {
  content: "\e75b";
}

.el-icon-collection:before {
  content: "\e75c";
}

.el-icon-receiving:before {
  content: "\e75d";
}

.el-icon-suitcase-1:before {
  content: "\e760";
}

.el-icon-suitcase:before {
  content: "\e761";
}

.el-icon-film:before {
  content: "\e763";
}

.el-icon-collection-tag:before {
  content: "\e765";
}

.el-icon-data-analysis:before {
  content: "\e766";
}

.el-icon-pie-chart:before {
  content: "\e767";
}

.el-icon-data-board:before {
  content: "\e768";
}

.el-icon-data-line:before {
  content: "\e76d";
}

.el-icon-reading:before {
  content: "\e769";
}

.el-icon-magic-stick:before {
  content: "\e76a";
}

.el-icon-coordinate:before {
  content: "\e76b";
}

.el-icon-mouse:before {
  content: "\e76c";
}

.el-icon-brush:before {
  content: "\e76e";
}

.el-icon-headset:before {
  content: "\e76f";
}

.el-icon-umbrella:before {
  content: "\e770";
}

.el-icon-scissors:before {
  content: "\e771";
}

.el-icon-mobile:before {
  content: "\e773";
}

.el-icon-attract:before {
  content: "\e774";
}

.el-icon-monitor:before {
  content: "\e775";
}

.el-icon-search:before {
  content: "\e778";
}

.el-icon-takeaway-box:before {
  content: "\e77a";
}

.el-icon-paperclip:before {
  content: "\e77d";
}

.el-icon-printer:before {
  content: "\e77e";
}

.el-icon-document-add:before {
  content: "\e782";
}

.el-icon-document:before {
  content: "\e785";
}

.el-icon-document-checked:before {
  content: "\e786";
}

.el-icon-document-copy:before {
  content: "\e787";
}

.el-icon-document-delete:before {
  content: "\e788";
}

.el-icon-document-remove:before {
  content: "\e789";
}

.el-icon-tickets:before {
  content: "\e78b";
}

.el-icon-folder-checked:before {
  content: "\e77f";
}

.el-icon-folder-delete:before {
  content: "\e780";
}

.el-icon-folder-remove:before {
  content: "\e781";
}

.el-icon-folder-add:before {
  content: "\e783";
}

.el-icon-folder-opened:before {
  content: "\e784";
}

.el-icon-folder:before {
  content: "\e78a";
}

.el-icon-edit-outline:before {
  content: "\e764";
}

.el-icon-edit:before {
  content: "\e78c";
}

.el-icon-date:before {
  content: "\e78e";
}

.el-icon-c-scale-to-original:before {
  content: "\e7c6";
}

.el-icon-view:before {
  content: "\e6ce";
}

.el-icon-loading:before {
  content: "\e6cf";
}

.el-icon-rank:before {
  content: "\e6d1";
}

.el-icon-sort-down:before {
  content: "\e7c4";
}

.el-icon-sort-up:before {
  content: "\e7c5";
}

.el-icon-sort:before {
  content: "\e6d2";
}

.el-icon-finished:before {
  content: "\e6cd";
}

.el-icon-refresh-left:before {
  content: "\e6c7";
}

.el-icon-refresh-right:before {
  content: "\e6c8";
}

.el-icon-refresh:before {
  content: "\e6d0";
}

.el-icon-video-play:before {
  content: "\e7c0";
}

.el-icon-video-pause:before {
  content: "\e7c1";
}

.el-icon-d-arrow-right:before {
  content: "\e6dc";
}

.el-icon-d-arrow-left:before {
  content: "\e6dd";
}

.el-icon-arrow-up:before {
  content: "\e6e1";
}

.el-icon-arrow-down:before {
  content: "\e6df";
}

.el-icon-arrow-right:before {
  content: "\e6e0";
}

.el-icon-arrow-left:before {
  content: "\e6de";
}

.el-icon-top-right:before {
  content: "\e6e7";
}

.el-icon-top-left:before {
  content: "\e6e8";
}

.el-icon-top:before {
  content: "\e6e6";
}

.el-icon-bottom:before {
  content: "\e6eb";
}

.el-icon-right:before {
  content: "\e6e9";
}

.el-icon-back:before {
  content: "\e6ea";
}

.el-icon-bottom-right:before {
  content: "\e6ec";
}

.el-icon-bottom-left:before {
  content: "\e6ed";
}

.el-icon-caret-top:before {
  content: "\e78f";
}

.el-icon-caret-bottom:before {
  content: "\e790";
}

.el-icon-caret-right:before {
  content: "\e791";
}

.el-icon-caret-left:before {
  content: "\e792";
}

.el-icon-d-caret:before {
  content: "\e79a";
}

.el-icon-share:before {
  content: "\e793";
}

.el-icon-menu:before {
  content: "\e798";
}

.el-icon-s-grid:before {
  content: "\e7a6";
}

.el-icon-s-check:before {
  content: "\e7a7";
}

.el-icon-s-data:before {
  content: "\e7a8";
}

.el-icon-s-opportunity:before {
  content: "\e7aa";
}

.el-icon-s-custom:before {
  content: "\e7ab";
}

.el-icon-s-claim:before {
  content: "\e7ad";
}

.el-icon-s-finance:before {
  content: "\e7ae";
}

.el-icon-s-comment:before {
  content: "\e7af";
}

.el-icon-s-flag:before {
  content: "\e7b0";
}

.el-icon-s-marketing:before {
  content: "\e7b1";
}

.el-icon-s-shop:before {
  content: "\e7b4";
}

.el-icon-s-open:before {
  content: "\e7b5";
}

.el-icon-s-management:before {
  content: "\e7b6";
}

.el-icon-s-ticket:before {
  content: "\e7b7";
}

.el-icon-s-release:before {
  content: "\e7b8";
}

.el-icon-s-home:before {
  content: "\e7b9";
}

.el-icon-s-promotion:before {
  content: "\e7ba";
}

.el-icon-s-operation:before {
  content: "\e7bb";
}

.el-icon-s-unfold:before {
  content: "\e7bc";
}

.el-icon-s-fold:before {
  content: "\e7a9";
}

.el-icon-s-platform:before {
  content: "\e7bd";
}

.el-icon-s-order:before {
  content: "\e7be";
}

.el-icon-s-cooperation:before {
  content: "\e7bf";
}

.el-icon-bell:before {
  content: "\e725";
}

.el-icon-message-solid:before {
  content: "\e799";
}

.el-icon-video-camera:before {
  content: "\e772";
}

.el-icon-video-camera-solid:before {
  content: "\e796";
}

.el-icon-camera:before {
  content: "\e779";
}

.el-icon-camera-solid:before {
  content: "\e79b";
}

.el-icon-download:before {
  content: "\e77c";
}

.el-icon-upload2:before {
  content: "\e77b";
}

.el-icon-upload:before {
  content: "\e7c3";
}

.el-icon-picture-outline-round:before {
  content: "\e75f";
}

.el-icon-picture-outline:before {
  content: "\e75e";
}

.el-icon-picture:before {
  content: "\e79f";
}

.el-icon-close:before {
  content: "\e6db";
}

.el-icon-check:before {
  content: "\e6da";
}

.el-icon-plus:before {
  content: "\e6d9";
}

.el-icon-minus:before {
  content: "\e6d8";
}

.el-icon-help:before {
  content: "\e73d";
}

.el-icon-s-help:before {
  content: "\e7b3";
}

.el-icon-circle-close:before {
  content: "\e78d";
}

.el-icon-circle-check:before {
  content: "\e720";
}

.el-icon-circle-plus-outline:before {
  content: "\e723";
}

.el-icon-remove-outline:before {
  content: "\e722";
}

.el-icon-zoom-out:before {
  content: "\e776";
}

.el-icon-zoom-in:before {
  content: "\e777";
}

.el-icon-error:before {
  content: "\e79d";
}

.el-icon-success:before {
  content: "\e79c";
}

.el-icon-circle-plus:before {
  content: "\e7a0";
}

.el-icon-remove:before {
  content: "\e7a2";
}

.el-icon-info:before {
  content: "\e7a1";
}

.el-icon-question:before {
  content: "\e7a4";
}

.el-icon-warning-outline:before {
  content: "\e6c9";
}

.el-icon-warning:before {
  content: "\e7a3";
}

.el-icon-goods:before {
  content: "\e7c2";
}

.el-icon-s-goods:before {
  content: "\e7b2";
}

.el-icon-star-off:before {
  content: "\e717";
}

.el-icon-star-on:before {
  content: "\e797";
}

.el-icon-more-outline:before {
  content: "\e6cc";
}

.el-icon-more:before {
  content: "\e794";
}

.el-icon-phone-outline:before {
  content: "\e6cb";
}

.el-icon-phone:before {
  content: "\e795";
}

.el-icon-user:before {
  content: "\e6e3";
}

.el-icon-user-solid:before {
  content: "\e7a5";
}

.el-icon-setting:before {
  content: "\e6ca";
}

.el-icon-s-tools:before {
  content: "\e7ac";
}

.el-icon-delete:before {
  content: "\e6d7";
}

.el-icon-delete-solid:before {
  content: "\e7c9";
}

.el-icon-eleme:before {
  content: "\e7c7";
}

.el-icon-platform-eleme:before {
  content: "\e7ca";
}

.el-icon-loading {
  animation: rotating 2s linear infinite;
}

.el-icon--right {
  margin-left: 5px;
}
.el-icon--left {
  margin-right: 5px;
}

@keyframes rotating {
  0% {
    transform: rotateZ(0deg);
  }
  100% {
    transform: rotateZ(360deg);
  }
}

```

### 从一个基础按钮组件开始分析

button.scss

至于为什么要从这个按钮开始分析呢？

我在看到 mixin 中定义了一个 `_button.scss` 文件, 这是 Element-ui 其它组件可没有的待遇

![](https://pic.imgdb.cn/item/6603e7579f345e8d0392b9df.png)

文件前缀 `_` 的含义如下：

在 SCSS (Sass的扩展语法) 中，文件名前面加上下划线 `_` 是一种**命名约定**，用来表示这个文件是一个**部分文件**（partial），而不是一个完整的样式表文件。

这种约定源自于Sass的一个特性，即它可以将样式表分解成多个小文件（称为部分文件），然后在一个主SCSS文件中通过 `@import` 指令将它们引入，从而构建出一个完整的样式表。

当在一个名为 `_button.scss` 的文件中定义了一个mixin，这个文件就是一个部分文件。它通常不直接被编译成CSS，而是在其他SCSS文件中通过 @import 引入，这样你就可以在多个地方重用这个mixin，而不需要重复编写相同的代码。

你可能有一个主样式表文件，在这个文件中会这样引入 _button.scss：

```css
@import "button";
```

这里的 "button" 就是 _button.scss 文件，不带下划线和扩展名。**Sass会自动查找名为 _button.scss 的文件**并将其内容包含进来。

这种使用下划线命名部分文件的做法有助于保持项目结构的清晰和组织，使得其他前端开发者能够很容易地理解哪些文件是用于被导入和重用的，哪些文件是最终生成CSS的文件。

继续看，发现其导入了很多 mixin，糟糕，看来不懂 mixin 是很难去读懂组件样式的，因此切换到去读懂 mixin 文件夹里面的 scss 文件

完整样式代码如下：

```scss
@charset "UTF-8";
@import "common/var";
@import "mixins/button";
@import "mixins/mixins";
@import "mixins/utils";

@include b(button) {
  display: inline-block;
  line-height: 1;
  white-space: nowrap;
  cursor: pointer;
  background: $--button-default-background-color;
  border: $--border-base;
  border-color: $--button-default-border-color;
  color: $--button-default-font-color;
  -webkit-appearance: none;
  text-align: center;
  box-sizing: border-box;
  outline: none;
  margin: 0;
  transition: .1s;
  font-weight: $--button-font-weight;
  @include utils-user-select(none);
  & + & {
    margin-left: 10px;
  }

  @include button-size($--button-padding-vertical, $--button-padding-horizontal, $--button-font-size, $--button-border-radius);

  &:hover,
  &:focus {
    color: $--color-primary;
    border-color: $--color-primary-light-7;
    background-color: $--color-primary-light-9;
  }

  &:active {
    color: mix($--color-black, $--color-primary, $--button-active-shade-percent);
    border-color: mix($--color-black, $--color-primary, $--button-active-shade-percent);
    outline: none;
  }

  &::-moz-focus-inner {
    border: 0;
  }

  & [class*="el-icon-"] {
    & + span {
      margin-left: 5px;
    }
  }

  @include when(plain) {
    &:hover,
    &:focus {
      background: $--color-white;
      border-color: $--color-primary;
      color: $--color-primary;
    }

    &:active {
      background: $--color-white;
      border-color: mix($--color-black, $--color-primary, $--button-active-shade-percent);
      color: mix($--color-black, $--color-primary, $--button-active-shade-percent);
      outline: none;
    }
  }

  @include when(active) {
    color: mix($--color-black, $--color-primary, $--button-active-shade-percent);
    border-color: mix($--color-black, $--color-primary, $--button-active-shade-percent);
  }

  @include when(disabled) {
    &,
    &:hover,
    &:focus {
      color: $--button-disabled-font-color;
      cursor: not-allowed;
      background-image: none;
      background-color: $--button-disabled-background-color;
      border-color: $--button-disabled-border-color;
    }

    &.el-button--text {
      background-color: transparent;
    }

    &.is-plain {
      &,
      &:hover,
      &:focus {
        background-color: $--color-white;
        border-color: $--button-disabled-border-color;
        color: $--button-disabled-font-color;
      }
    }
  }

  @include when(loading) {
    position: relative;
    pointer-events: none;

    &:before {
      pointer-events: none;
      content: '';
      position: absolute;
      left: -1px;
      top: -1px;
      right: -1px;
      bottom: -1px;
      border-radius: inherit;
      background-color: rgba(255,255,255,.35);
    }
  }
  @include when(round) {
    border-radius: 20px;
    padding: 12px 23px;
  }
  @include when(circle) {
    border-radius: 50%;
    padding: $--button-padding-vertical;
  }
  @include m(primary) {
    @include button-variant($--button-primary-font-color, $--button-primary-background-color, $--button-primary-border-color);
  }
  @include m(success) {
    @include button-variant($--button-success-font-color, $--button-success-background-color, $--button-success-border-color);
  }
  @include m(warning) {
    @include button-variant($--button-warning-font-color, $--button-warning-background-color, $--button-warning-border-color);
  }
  @include m(danger) {
    @include button-variant($--button-danger-font-color, $--button-danger-background-color, $--button-danger-border-color);
  }
  @include m(info) {
    @include button-variant($--button-info-font-color, $--button-info-background-color, $--button-info-border-color);
  }
  @include m(medium) {
    @include button-size($--button-medium-padding-vertical, $--button-medium-padding-horizontal, $--button-medium-font-size, $--button-medium-border-radius);
    @include when(circle) {
      padding: $--button-medium-padding-vertical;
    }
  }
  @include m(small) {
    @include button-size($--button-small-padding-vertical, $--button-small-padding-horizontal, $--button-small-font-size, $--button-small-border-radius);
    @include when(circle) {
      padding: $--button-small-padding-vertical;
    }
  }
  @include m(mini) {
    @include button-size($--button-mini-padding-vertical, $--button-mini-padding-horizontal, $--button-mini-font-size, $--button-mini-border-radius);
    @include when(circle) {
      padding: $--button-mini-padding-vertical;
    }
  }
  @include m(text) {
    border-color: transparent;
    color: $--color-primary;
    background: transparent;
    padding-left: 0;
    padding-right: 0;

    &:hover,
    &:focus {
      color: mix($--color-white, $--color-primary, $--button-hover-tint-percent);
      border-color: transparent;
      background-color: transparent;
    }
    &:active {
      color: mix($--color-black, $--color-primary, $--button-active-shade-percent);
      border-color: transparent;
      background-color: transparent;
    }

    &.is-disabled,
    &.is-disabled:hover,
    &.is-disabled:focus {
      border-color: transparent;
    }
  }
}

@include b(button-group) {
  @include utils-clearfix;
  display: inline-block;
  vertical-align: middle;

  & > .el-button {
    float: left;
    position: relative;
    & + .el-button {
      margin-left: 0;
    }
    &.is-disabled {
      z-index: 1;
    }
    &:first-child {
      border-top-right-radius: 0;
      border-bottom-right-radius: 0;
    }
    &:last-child {
      border-top-left-radius: 0;
      border-bottom-left-radius: 0;
    }
    &:first-child:last-child {
      border-top-right-radius: $--button-border-radius;
      border-bottom-right-radius: $--button-border-radius;
      border-top-left-radius: $--button-border-radius;
      border-bottom-left-radius: $--button-border-radius;

      &.is-round {
        border-radius: 20px;
      }

      &.is-circle {
        border-radius: 50%;
      }
    }
    &:not(:first-child):not(:last-child) {
      border-radius: 0;
    }
    &:not(:last-child) {
      margin-right: -1px;
    }

    &:not(.is-disabled) {
      &:hover,
      &:focus,
      &:active {
        z-index: 1;
      }
    }

    @include when(active) {
      z-index: 1;
    }
  }

  & > .el-dropdown {
    & > .el-button {
      border-top-left-radius: 0;
      border-bottom-left-radius: 0;
      border-left-color: rgba($--color-white, 0.5);
    }
  }

  @each $type in (primary, success, warning, danger, info) {
    .el-button--#{$type} {
      &:first-child {
        border-right-color: rgba($--color-white, 0.5);
      }
      &:last-child {
        border-left-color: rgba($--color-white, 0.5);
      }
      &:not(:first-child):not(:last-child) {
        border-left-color: rgba($--color-white, 0.5);
        border-right-color: rgba($--color-white, 0.5);
      }
    }
  }
}
```

### mixins 中的文件解读

一共是这样几个

```sh
mixins
  - _button.scss
  - config.scss
  - function.scss
  - mixins.scss
  - utils.scss
```

`config.scss`

这里进行了一些配置

这些变量在 Element UI 的源码中非常重要，因为它们定义了组件的类名结构。

```scss
$namespace: 'el';
$element-separator: '__';
$modifier-separator: '--';
$state-prefix: 'is-';
```

1. $namespace: 'el';

这个变量定义了 Element UI 组件的基础命名空间。在 CSS 中，这个命名空间会被用作组件类名的前缀。例如，如果你有一个按钮组件，它的类名可能会是 el-button。这样做的好处是可以帮助避免全局命名冲突，同时提供了一个清晰的、与 Element UI 相关的样式作用域。

2. $element-separator: '__';
这个变量定义了 Element UI 组件内部元素的分隔符。在 Element UI 的类名中，当你需要表示一个组件内部的子元素时，你会使用这个分隔符。例如，如果你有一个带有图标的按钮，图标部分的类名可能会是 el-button__icon。这样的命名方式有助于区分组件的不同部分，并且使得组件的结构更加清晰。

3. $modifier-separator: '--';
这个变量定义了 Element UI 组件修饰符（modifier）的分隔符。修饰符用于改变组件的样式或行为。例如，如果你想要一个圆角按钮，你可能会使用 el-button--circle。这里的 -- 就是修饰符分隔符，它将修饰符与组件的基础类名分开。

4. $state-prefix: 'is-';
这个变量定义了 Element UI 组件状态前缀。状态类用于表示组件的不同状态，比如禁用状态、激活状态等。例如，如果一个按钮是禁用的，它的类名可能会包含 is-disabled。这个前缀 is- 有助于快速识别状态相关的类名，并且保持了命名的一致性。

`function.scss`

可以看到该函数的描述是 `BEM support Func`，那么什么是BEM呢？

[点击阅读官网](https://en.bem.info/methodology/quick-star)

```css
@import "config";

/* BEM support Func
 -------------------------- */
@function selectorToString($selector) {
  $selector: inspect($selector);
  $selector: str-slice($selector, 2, -2);
  @return $selector;
}

@function containsModifier($selector) {
  $selector: selectorToString($selector);

  @if str-index($selector, $modifier-separator) {
    @return true;
  } @else {
    @return false;
  }
}

@function containWhenFlag($selector) {
  $selector: selectorToString($selector);

  @if str-index($selector, '.' + $state-prefix) {
    @return true
  } @else {
    @return false
  }
}

@function containPseudoClass($selector) {
  $selector: selectorToString($selector);

  @if str-index($selector, ':') {
    @return true
  } @else {
    @return false
  }
}

@function hitAllSpecialNestRule($selector) {

  @return containsModifier($selector) or containWhenFlag($selector) or containPseudoClass($selector);
}
```

理解这个函数的关键就是知道 `inspect` 是什么？

在其它的文件中，以及这个函数文件中，并没有对该函数进行调用，因此这应该是 scss 内置的一个函数，于是来到官网，[点击查看 inspect 这个语法点](https://www.sass.hk/docs/)

![果然被我找到了](https://pic.imgdb.cn/item/660407e69f345e8d03812814.png)

> Maps represent an association between keys and values, where keys are used to look up values. They make it easy to collect values into named groups and access those groups dynamically. They have no direct parallel in CSS, although they’re syntactically similar to media query expressions: scss $map: (key1: value1, key2: value2, key3: value3); Unlike lists, maps must always be surrounded by parentheses and must always be comma-separated. Both the keys and values in maps can be any SassScript object. A map may only have one value associated with a given key (although that value may be a list). A given value may be associated with many keys, though. Like lists, maps are mostly manipulated using SassScript functions. The map-get function looks up values in a map and the map-merge function adds values to a map. The @each directive can be used to add styles for each key/value pair in a map. The order of pairs in a map is always the same as when the map was created. Maps can also be used anywhere lists can. When used by a list function, a map is treated as a list of pairs. For example, (key1: value1, key2: value2) would be treated as the nested list key1 value1, key2 value2 by list functions. Lists cannot be treated as maps, though, with the exception of the empty list. () represents both a map with no key/value pairs and a list with no elements. Note that map keys can be any Sass data type (even another map) and the syntax for declaring a map allows arbitrary SassScript expressions that will be evaluated to determine the key. Maps cannot be converted to plain CSS. Using one as the value of a variable or an argument to a CSS function will cause an error. Use the inspect($value) function to produce an output string useful for debugging maps.

翻译：

在 Sass 中，映射（Maps）表示键（keys）和值（values）之间的关联，其中键用于查找值。映射使得将值收集到命名的组中并动态访问这些组变得非常容易。尽管它们在语法上与 CSS 的媒体查询表达式相似，但映射在 CSS 中没有直接对应的概念：

```scss
$map: (key1: value1, key2: value2, key3: value3);
```

与列表（lists）不同，映射必须始终用括号包围，并且必须用逗号分隔。映射中的键和值可以是任何 SassScript 对象。一个映射对于给定的键只能有一个关联的值（尽管该值可以是一个列表）。然而，一个给定的值可以与多个键关联。

与列表类似，映射主要通过 SassScript 函数进行操作。`map-get` 函数用于在映射中查找值，而 `map-merge` 函数用于向映射添加值。`@each` 指令可以用来为映射中的每个键/值对添加样式。映射中的键值对的顺序始终与创建映射时的顺序相同。映射还可以在任何列表可以被使用的地方使用。当映射被列表函数使用时，它会被视为键值对的嵌套列表。例如，`(key1: value1, key2: value2)` 会被列表函数视为嵌套列表 `key1 value1, key2 value2`。然而，列表不能被视为映射，例外的是空列表。`()` 既表示没有键值对的映射，也表示没有元素的列表。

需要注意的是，映射的键可以是任何 Sass 数据类型（甚至是另一个映射），并且声明映射的语法允许使用任意的 SassScript 表达式，这些表达式将被求值以确定键。映射不能转换为纯 CSS。将映射用作变量的值或 CSS 函数的参数将导致错误。使用 `inspect($value)` 函数可以产生用于调试映射的输出字符串。

```scss
// 示例：使用 map-get 函数获取映射中的值
$my-map: (primary: #ff0000, secondary: #00ff00, tertiary: #0000ff);
color: map-get($my-map, primary); // 返回 #ff0000

// 示例：使用 @each 指令遍历映射
@each $key, $value in $my-map {
  .#{$key}-text {
    color: $value;
  }
}
```

上面的代码会生成以下 CSS：

```css
.primary-text {
  color: #ff0000;
}
.secondary-text {
  color: #00ff00;
}
.tertiary-text {
  color: #0000ff;
}
```

如上展示了如何使用 `@each` 指令遍历映射并生成对应的 CSS 类。

接下来对这些函数进行一个深入的学习，看他是如何来支持 BEM 的：

BEM（Block Element Modifier）是一种 CSS 方法论，用于创建可重用、可维护的样式表。它通过将页面元素分为不同的块（Blocks）、元素（Elements）和修饰符（Modifiers），来组织和命名 CSS 类。这种方法有助于避免类名冲突，提高代码的可读性和可维护性。

`function.scss` 文件中，定义了几个函数，这些函数用于处理和检查 CSS 选择器，以支持 BEM 方法论。

1. `@function selectorToString($selector)`:
   这个函数接收一个选择器作为参数，并将其转换为字符串格式。它使用 `inspect` 函数来获取参数的字符串表示，然后使用 `str-slice` 函数去除选择器字符串首尾的括号。这个函数是其他函数的基础，因为它将选择器处理成字符串，以便进行后续的字符串操作。

2. `@function containsModifier($selector)`:
   此函数检查给定的选择器是否包含 BEM 修饰符分隔符（通常是 `--`）。它调用 `selectorToString` 函数将选择器转换为字符串，然后使用 `str-index` 函数查找字符串中是否包含修饰符分隔符。如果找到，函数返回 `true`，表示选择器包含修饰符；否则返回 `false`。

3. `@function containWhenFlag($selector)`:
   这个函数用于检查选择器是否包含 BEM 状态前缀（通常是 `is-`）。它同样调用 `selectorToString` 函数处理选择器，然后使用 `str-index` 函数查找字符串中是否包含状态前缀。如果包含，返回 `true`；否则返回 `false`。

4. `@function containPseudoClass($selector)`:
   此函数检查选择器是否包含伪类。它通过查找选择器字符串中是否包含冒号（`:`）来判断。如果包含伪类，返回 `true`；否则返回 `false`。

5. `@function hitAllSpecialNestRule($selector)`:
   这个函数是一个组合检查，用于判断选择器是否包含任何特殊的嵌套规则，包括修饰符、状态标志或伪类。它通过组合调用前面定义的三个函数 `containsModifier`、`containWhenFlag` 和 `containPseudoClass` 来实现。如果选择器包含这三者中的任何一个，函数返回 `true`；否则返回 `false`。

这些函数的目的是为了在编写 CSS 时支持 BEM 方法论，帮助开发者识别和管理 BEM 类名中的特定模式。通过这些函数，可以更容易地编写符合 BEM 规范的样式，从而提高 CSS 代码的组织性和可维护性。

接下来看到 mixin 的 BEM 具体实现：


## Vue.js


## gulp


## TypeScript