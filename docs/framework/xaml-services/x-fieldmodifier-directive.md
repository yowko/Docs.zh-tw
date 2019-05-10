---
title: x:FieldModifier 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 0394522b8a006d6b187219c8ef7dfccd6556ffca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617070"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier 指示詞
修改 XAML 編譯行為，以便以定義已命名的物件參考的欄位<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>而不是存取<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>預設行為。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*Public*|您將傳遞至指定的確切字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>與<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>各有不同，會使用的程式碼後置程式設計語言而定。 請參閱＜備註＞。|  
  
## <a name="dependencies"></a>相依性  
 如果使用 XAML 生產`x:FieldModifier`該 XAML 生產的根項目必須宣告隨時隨地[X:class 指示詞](x-class-directive.md)。  
  
## <a name="remarks"></a>備註  
 `x:FieldModifier` 不相關的宣告類別或其成員的一般存取層級。 當屬於 XAML 生產的特定 XAML 物件處理，而變成可能可以存取應用程式的物件圖形中的物件，它是只會針對 XAML 處理行為的相關。 根據預設，這類物件的欄位參考會保留私用，這可防止控制項的取用者直接修改的物件圖形。 相反地，控制項的取用者會藉由使用標準模式會啟用程式設計模型，例如取得版面配置根目錄中，子系項目集合，專用的公用屬性，修改的物件圖形，並以此類推。  
  
 值`x:FieldModifier`屬性而異的程式設計語言，與特定架構可以改變它的目的。 要使用的字串取決於各種語言的實作方式及其<xref:System.CodeDom.Compiler.CodeDomProvider>和類型轉換器，它會傳回定義的意義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>和<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>，以及該語言是否區分大小寫。  
  
- 適用於 C#，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>是`public`。  
  
- 適用於 Microsoft Visual Basic.NET，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>是`Public`。  
  
- 針對[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，XAML 的任何目標目前存在; 因此，要傳遞的字串未定義。  
  
 您也可以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>(`internal`在C#， `Friend` Visual Basic 中) 但指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>不尋常因為`NotPublic`行為已是預設值。  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> 是預設行為，因為它是不頻繁的編譯 XAML 的組件外部的程式碼需要存取 XAML 建立的項目。 WPF 與 XAML 編譯行為的安全性架構會宣告為公用，儲存項目執行個體的欄位，除非您特別設定`x:FieldModifier`為允許公用存取。  
  
 `x:FieldModifier` 才有意義之項目的[X:name 指示詞](x-name-directive.md)因為該名稱用來參考欄位之後它是公用。  
  
 根據預設，部分類別的根項目是公用的;不過，您可以使其非公用利用[X:classmodifier 指示詞](x-classmodifier-directive.md)。 [X:classmodifier 指示詞](x-classmodifier-directive.md)也會影響根項目類別的執行個體的存取層級。 您可以將兩者放`x:Name`並`x:FieldModifier`上的根項目，但這只會使公用欄位複本的根元素，則為 true 的根項目類別的存取層級仍受到[X:classmodifier 指示詞](x-classmodifier-directive.md)。  
  
## <a name="see-also"></a>另請參閱

- [WPF 的 XAML 和自訂類別](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [WPF 中的程式碼後置和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name 指示詞](x-name-directive.md)
- [建置 WPF 應用程式 (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier 指示詞](x-classmodifier-directive.md)
