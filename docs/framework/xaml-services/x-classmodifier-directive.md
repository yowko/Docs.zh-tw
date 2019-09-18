---
title: x:ClassModifier 指示詞
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 5daff0567c1b1415fe994f6e39b4079cb2ab7346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053824"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier 指示詞
當也提供時`x:Class` ，修改 XAML 編譯行為。 具體而言，它不會建立`class` `Public`具有存取層級的部分（預設值），而`x:Class`是使用`NotPublic`存取層級建立所提供的。 這個行為會影響所產生元件中類別的存取層級。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*NotPublic*|視您使用的程式碼後<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>置<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>程式語言而定，要傳遞來指定和的確切字串會有所不同。 請參閱＜備註＞。|  
  
## <a name="dependencies"></a>相依性  
 您也必須在相同的元素上提供[x：Class](x-class-directive.md) ，而且該元素必須是頁面中的根項目。 如需詳細資訊，請參閱 < [ \[MS-XAML\]區段 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="remarks"></a>備註  
 .NET Framework XAML 服務`x:ClassModifier`使用量中的值會因程式設計語言而異。 要使用的字串取決於每種語言如何執行<xref:System.CodeDom.Compiler.CodeDomProvider>其和它所傳回的型別轉換器，以<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>定義<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的意義，以及該語言是否區分大小寫。  
  
- 若C#為，要傳遞以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>的字串是。 `internal`  
  
- 若為 Microsoft Visual Basic .net，要傳遞以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>的字串是。 `Friend`  
  
- 針對C++/cli，不存在支援編譯 XAML 的目標。因此，未指定要傳遞的值。  
  
 您也可以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> （`public`在C#Visual Basic `Public`中）; 不過，指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>不常完成，因為<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>已經是預設行為。  
  
 具有對等使用者程式碼存取層級限制的其他值`private` （ C#例如中的）與`x:ClassModifier`不相關，因為 XAML 中不支援嵌套類別參考，因此<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>修飾詞的效果相同.  
  
## <a name="security-notes"></a>安全性注意事項  
 如中`x:ClassModifier`所宣告的存取層級，仍然受限於特定架構及其功能的轉譯。 Wpf 包含載入和具現化類型的`x:ClassModifier`功能`internal`，其中是，如果透過 pack URI 參考從 WPF 資源參考該類別。 這種情況的結果可能是因為其他架構所實行的其他架構，而不依賴`x:ClassModifier`來封鎖所有可能的具現化嘗試。  
  
## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](x-class-directive.md)
- [WPF 中的程式碼後置和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier 指示詞](x-fieldmodifier-directive.md)
- [安全性（WPF）](../wpf/security-wpf.md)
- [從 WPF 移轉至 System.Xaml 的類型](types-migrated-from-wpf-to-system-xaml.md)
