---
title: x:FieldModifier 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 646ad1ca99d83f9fb2994f3c394eca27a60c0eac
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484727"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier 指示詞
修改 XAML 編譯行為, 讓命名物件參考的欄位是以存取<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>來定義, 而<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>不是使用預設行為。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*Public*|視所使用的程式碼後<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>置<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>程式語言而定, 您傳遞來指定與的確切字串會有所不同。 請參閱＜備註＞。|  
  
## <a name="dependencies"></a>相依性  
 如果 xaml 生產環境使用`x:FieldModifier`任何位置, 則該 xaml 生產環境的根項目必須宣告[x:Class](x-class-directive.md)指示詞。  
  
## <a name="remarks"></a>備註  
 `x:FieldModifier`與宣告類別或其成員的一般存取層級無關。 只有在處理 XAML 生產中的特定 XAML 物件時, 它才與 XAML 處理行為有關, 它會成為在應用程式的物件圖形中可能可存取的物件。 根據預設, 這類物件的欄位參考會保持為私用, 以防止控制取用者直接修改物件圖形。 相反地, 控制取用者應該使用由程式設計模型啟用的標準模式 (例如, 藉由取得版面配置根、子專案集合、專用的公用屬性等等) 來修改物件圖形。  
  
 `x:FieldModifier`屬性的值會因程式設計語言而異, 而且其目的可能會因特定架構而異。 要使用的字串取決於每種語言如何執行<xref:System.CodeDom.Compiler.CodeDomProvider>其和它所傳回的型別轉換器, 以<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>定義<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>和的意義, 以及該語言是否區分大小寫。  
  
- 若C#為, 要傳遞以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的字串是。 `public`  
  
- 若為 Microsoft Visual Basic .net, 要傳遞以指定<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>的字串是。 `Public`  
  
- 針對C++/CLI, XAML 目前不存在任何目標;因此, 要傳遞的字串未定義。  
  
 您也可以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal`在C#Visual Basic `Friend`中), 但指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>不尋常, `NotPublic`因為行為已經是預設值。  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是預設行為, 因為編譯 XAML 之元件外部的程式碼需要存取 XAML 所建立的專案。 WPF 安全性架構與 XAML 編譯行為並不會宣告將元素實例儲存為公用的欄位, 除非您特別將`x:FieldModifier`設定為允許公用存取。  
  
 `x:FieldModifier`僅與具有[x:Name](x-name-directive.md)指示詞的元素相關, 因為該名稱是在公用後用來參考欄位。  
  
 根據預設, 根項目的部分類別是公用的;不過, 您可以使用[x:ClassModifier](x-classmodifier-directive.md)指示詞將它設為非公用。 [X:ClassModifier](x-classmodifier-directive.md)指示詞也會影響根項目類別之實例的存取層級。 您可以將`x:Name`和`x:FieldModifier`放在根項目上, 但這只會建立根項目的公用欄位複本, 而真正的根項目類別存取層級仍由[x:ClassModifier](x-classmodifier-directive.md)指示詞控制。  
  
## <a name="see-also"></a>另請參閱

- [WPF 的 XAML 和自訂類別](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [WPF 中的程式碼後置和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name 指示詞](x-name-directive.md)
- [建置 WPF 應用程式 (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier 指示詞](x-classmodifier-directive.md)
