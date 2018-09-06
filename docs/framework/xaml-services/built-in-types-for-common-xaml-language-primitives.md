---
title: 通用 XAML 語言基本類型的內建類型
ms.date: 03/30/2017
helpviewer_keywords:
- XAML language primitives [XAML Services]
- XAML [XAML Services], built-in types
- x:String [XAML Services]
- x:TimeSpan [XAML Services]
- x:Byte [XAML Services]
- x:Double [XAML Services]
- XAML [XAML Services], types
- x:Uri [XAML Services]
- XAML built-in types [XAML Services]
- x:Int64 [XAML Services]
- x:Single [XAML Services]
- x:Int32 [XAML Services]
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
ms.openlocfilehash: f6225dfcc02b90da58ccafd5c70726b6f80f29d4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731348"
---
# <a name="built-in-types-for-common-xaml-language-primitives"></a>通用 XAML 語言基本類型的內建類型
XAML 2009 引進數種資料類型的 XAML 語言層級支援，而這些資料類型是 Common Language Runtime (CLR) 和其他程式設計語言中的常用基本類型。 XAML 2009 新增下列基本類型的支援： `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte`和 `x:Array`。  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## <a name="previous-techniques-for-language-primitives-in-xaml-markup"></a>XAML 標記中語言基本類型的先前技術  
 在舊版 WPF 的 XAML 中，對應內含 .NET Framework 之 CLR 基本類型定義類別的組件和命名空間，即可參考 CLR 語言基本類型。 其中大部分是在 mscorlib 組件和 <xref:System> 命名空間中。 例如，若要使用 <xref:System.Int32>，您可以宣告下列對應 (具有後面顯示的範例使用方式)：  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
xmlns:sys="clr-namespace:System;assembly=mscorlib">  
  <Application.Resources>  
    <sys:Int32 x:Key="intMeaning">42</sys:Int32>  
  </Application.Resources>  
</Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## <a name="xaml-2009-language-primitives"></a>XAML 2009 語言基本類型  
 根據慣例，會顯示 XAML 的語言基本類型和所有其他 XAML 語言項目 (包括 `x:` 前置詞)。 這是一般如何在實際標記中使用 XAML 語言項目。 WPF 和 XAML 規格中 XAML 概念文件中會遵循這個慣例。  
  
### <a name="xobject"></a>x:Object  
 對於 CLR 支援， `x:Object` 基本類型對應至 <xref:System.Object>。  
  
 此基本類型通常不會用於應用程式標記中，但在某些情況下可能十分有用，例如檢查 XAML 類型系統中的指派性。  
  
### <a name="xboolean"></a>x:Boolean  
 對於 CLR 支援， `x:Boolean` 基本類型對應至 <xref:System.Boolean>。  
  
 XAML 將 `x:Boolean` 的值剖析為不區分大小寫。 請注意， `x:Bool` 不是可接受的替代方案。 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.17 和 5.4.11 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xchar"></a>x:Char  
 對於 CLR 支援， `x:Char` 基本類型對應至 <xref:System.Char>。  
  
 字串和 char 類型會與 XML 層級之檔案的整體編碼間互動。 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.7 和 5.4.1 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xstring"></a>x:String  
 對於 CLR 支援， `x:String` 基本類型對應至 <xref:System.String>。  
  
 字串和 char 類型會與 XML 層級之檔案的整體編碼間互動。 如需 XAML 語言規格定義，請參閱[ \[MS XAML\] 5.2.6](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xdecimal"></a>x:Decimal  
 對於 CLR 支援， `x:Decimal` 基本類型對應至 <xref:System.Decimal>。  
  
 請注意，XAML 剖析原本是在 `en-US` 文化特性下執行。 在 `en-US` 文化特性下，小數點之元件的正確分隔符號一律是句號 (`.`)，不論開發環境的文化特性設定為何，或在執行階段載入 XAML 之最終用戶端目標的文化特性設定為何。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.14 和 5.4.8 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xsingle"></a>x:Single  
 對於 CLR 支援， `x:Single` 基本類型對應至 <xref:System.Single>。  
  
 除了數值之外，`x:Single` 的文字語法也允許語彙基元 `Infinity``-Infinity` 和 `NaN`。 這些語彙基元視為區分大小寫。  
  
 如果文字語法中的第一個字元是`x:Single` 或 `e` ， `E`可以支援科學標記法格式的值。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.8 和 5.4.2 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xdouble"></a>x:Double  
 對於 CLR 支援， `x:Double` 基本類型對應至 <xref:System.Double>。  
  
 除了數值之外，`x:Double` 的文字語法還允許語彙基元 `Infinity``-Infinity` 和 `NaN`。 這些語彙基元視為區分大小寫。  
  
 `x:Double` 可以支援科學標記法格式的值。 使用字元 `e` 或 `E` 導入指數部分。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.9 和 5.4.3 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xint16"></a>x:Int16  
 對於 CLR 支援， `x:Int16` 基本類型對應至 <xref:System.Int16> ，並將 `x:Int16` 視為帶正負號。 在 XAML 中，文字語法中沒有加號 (`+`) 隱含為正數的帶正負號值。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.11 和 5.4.5 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xint32"></a>x:Int32  
 對於 CLR 支援， `x:Int32` 基本類型對應至 <xref:System.Int32>。 `x:Int32` 視為帶正負號。 在 XAML 中，文字語法中沒有加號 (`+`) 隱含為正數的帶正負號值。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.12 和 5.4.6 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xint64"></a>x:Int64  
 對於 CLR 支援， `x:Int64` 基本類型對應至 <xref:System.Int64>。 `x:Int64` 視為帶正負號。 在 XAML 中，文字語法中沒有加號 (`+`) 隱含為正數的帶正負號值。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.13 和 5.4.7 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xtimespan"></a>x:TimeSpan  
 對於 CLR 支援， `x:TimeSpan` 基本類型對應至 <xref:System.TimeSpan>。  
  
 請注意，時間-日期 (time-date) 格式的 XAML 剖析原本是在 `en-US` 文化特性下執行。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.16 和 5.4.10 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xuri"></a>x:Uri  
 對於 CLR 支援， `x:Uri` 基本類型對應至 <xref:System.Uri>。  
  
 檢查通訊協定是否為 `x:Uri`之 XAML 定義的一部分。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.15 和 5.4.9 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xbyte"></a>x:Byte  
 對於 CLR 支援， `x:Byte` 基本類型對應至 <xref:System.Byte>。 A <xref:System.Byte>  /  `x:Byte`處理為不帶正負號。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\]第 5.2.10 和 5.4.4 節](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
### <a name="xarray"></a>x:Array  
 對於 CLR 支援， `x:Array` 基本類型對應至 <xref:System.Array>。  
  
 使用標記延伸語法，即可在 XAML 2006 中定義陣列；不過，XAML 2009 語法是不需要存取標記延伸的語言定義基本類型。 如需 XAML 2006 支援的詳細資訊，請參閱 [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md)。  
  
 如需 XAML 語言規格定義，請參閱[ \[MS XAML\] 5.2.18](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
<a name="wpf_support"></a>   
## <a name="wpf-support"></a>WPF 支援  
 在 WPF 中，您可以使用 XAML 2009 功能，但只能針對未編譯標記的 XAML。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。  
  
 您可以在其中使用 XAML 2009 功能與 WPF 的情況是您編寫鬆散的 XAML，然後將該 XAML 載入 WPF 執行階段和物件圖與至<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>。 WPF<xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType>及其<xref:System.Windows.Markup.XamlReader.Load%2A>可以 XAML 2009 語言關鍵字和功能處理為有效的物件圖表示法。
