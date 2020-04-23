---
title: x:FieldModifier 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 3e104b4c464d545e048f29901701c1c3dbb68229
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071525"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier 指示詞
修改 XAML 編譯行為,<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>以便使用 訪問而不是默認行為定義命名<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>物件引用的 欄位。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|*公開*|傳遞給指定的<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>確切字串因<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>所使用的代碼後面程式設計語言而異。 請參閱＜備註＞。|

## <a name="dependencies"></a>相依性

 如果 XAML`x:FieldModifier`生產 在任何地方使用,則 XAML 生產的根元素必須聲明[x:類指令](xclass-directive.md)。

## <a name="remarks"></a>備註

`x:FieldModifier`與聲明類或其成員的一般訪問級別無關。 它僅與 XAML 處理行為相關,因為處理屬於 XAML 生產一部分的特定 XAML 物件,並成為在應用程式的物件圖中可能可存取的物件。 默認情況下,此類物件的欄位引用保持私有,這可以防止控件消費者直接修改物件圖。 相反,控制使用者應該使用程式設計模型啟用的標準模式來修改物件圖,例如透過獲取佈局根、子元素集合、專用公共屬性等。

`x:FieldModifier`屬性的值因程式設計語言而異,並且其用途可能因特定框架而異。 要使用的字串取決於每種語言如何實現其<xref:System.CodeDom.Compiler.CodeDomProvider>和返回的類型轉換器來定義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType><xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的含義,以及該語言是否區分大小寫。

- 對 C#,要傳遞到指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的字串為`public`。

- 對於 Microsoft Visual Basic .NET,要傳遞<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>要`Public`指定的字串為 。

- 對於C++/CLI,目前不存在 XAML 的目標;因此,要傳遞的字串未定義。

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>您還可以指定(`internal`在 C# 中`Friend`,在 Visual Basic<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>中),`NotPublic`但指定是不尋常的,因為行為已經是預設值。

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是默認行為,因為編譯 XAML 的程式集外部的代碼很少需要訪問 XAML 創建的元素。 WPF 安全體系結構以及 XAML 編譯行為不會聲明存儲元素實例的欄位為公共,除非`x:FieldModifier`您專門設置 允許公共存取。

`x:FieldModifier`僅與[具有 x:name 指令](xname-directive.md)的元素相關,因為該名稱用於在字段公開後引用該欄位。

默認情況下,根元素的部分類是公共的;因此,根元素的部分類為公共類。但是,您可以使用[x:Class 修改器指令](xclassmodifier-directive.md)將其非公開。 [x:Class 修改器指令](xclassmodifier-directive.md)還影響根元素類實例的訪問級別。 您可以將和`x:FieldModifier``x:Name`放在根元素上,但這僅使根元素的公共欄位副本,真正的根元素類存取級別仍由[x:Class 修改器指令](xclassmodifier-directive.md)控制。

## <a name="see-also"></a>另請參閱

- [WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [WPF 中的程式碼後置和 XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name 指示詞](xname-directive.md)
- [建置 WPF 應用程式 (WPF)](../../framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier 指示詞](xclassmodifier-directive.md)
