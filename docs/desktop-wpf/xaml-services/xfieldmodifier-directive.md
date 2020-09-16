---
title: x:FieldModifier 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 4e67a6dac49b8d6a7d316526f99a1519b08fd68b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554471"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier 指示詞
修改 XAML 編譯行為，以便將命名物件參考的欄位定義為具有 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 存取權，而不是使用 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 預設行為。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|*公開*|<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 視使用的程式碼後端程式設計語言而定，您傳遞給指定和的確切字串會有所不同。 請參閱＜備註＞。|

## <a name="dependencies"></a>相依性

 如果 XAML 生產環境使用 `x:FieldModifier` 任何位置，則該 xaml 生產的根項目必須宣告 [x：Class](xclass-directive.md)指示詞。

## <a name="remarks"></a>備註

`x:FieldModifier` 與宣告類別或其成員的一般存取層級無關。 只有在處理屬於 XAML 生產的特定 XAML 物件時，它才會與 XAML 處理行為相關，並且會成為可能在應用程式的物件圖形中存取的物件。 根據預設，這類物件的欄位參考會保留為私用，以防止控制取用者直接修改物件圖形。 相反地，控制取用者應該使用程式設計模型所啟用的標準模式來修改物件圖形，例如藉由取得配置根、子項目集合、專用公用屬性等。

`x:FieldModifier`屬性（attribute）的值會因程式設計語言而異，而其用途在特定架構中會有所不同。 要使用的字串取決於每個語言的實作為方式， <xref:System.CodeDom.Compiler.CodeDomProvider> 以及它所傳回的類型轉換器來定義和的意義 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ，以及該語言是否區分大小寫。

- 若為 c #，要傳遞給指定的字串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 為 `public` 。

- 針對 Microsoft Visual Basic .NET，要傳遞給指定的字串 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> 為 `Public` 。

- 針對 c + +/CLI，目前沒有 XAML 的目標存在;因此，要傳遞的字串是未定義的。

您也可以 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `internal` 在 Visual Basic) 中，以 c # 指定 (， `Friend` 但 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 因為 `NotPublic` 行為已是預設值，所以指定為不尋常。

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 是預設行為，因為編譯 XAML 的元件之外的程式碼需要存取 XAML 建立的元素。 除非您特別將設定 `x:FieldModifier` 為允許公用存取，否則 WPF 安全性架構與 XAML 編譯行為將不會宣告將專案實例儲存為公用的欄位。

`x:FieldModifier` 僅與具有 [x：Name](xname-directive.md) 指示詞的元素相關，因為該名稱是在公用之後用來參考欄位。

根據預設，根項目的部分類別是公用的，不過，您可以使用 [x:ClassModifier](xclassmodifier-directive.md)指示詞將它設為非公用。 [X:ClassModifier](xclassmodifier-directive.md)指示詞也會影響根項目類別之實例的存取層級。 您可以在 `x:Name` `x:FieldModifier` 根項目上放置和，但這只會建立根項目的公用欄位複本，而真正的根項目類別存取層級仍由 [x:ClassModifier](xclassmodifier-directive.md)指示詞控制。

## <a name="see-also"></a>另請參閱

- [WPF 的 XAML 和自訂類別](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [WPF 中的程式碼後置和 XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [x:Name 指示詞](xname-directive.md)
- [ (WPF) 建立 WPF 應用程式 ](/dotnet/desktop/wpf/app-development/building-a-wpf-application-wpf)
- [x:ClassModifier 指示詞](xclassmodifier-directive.md)
