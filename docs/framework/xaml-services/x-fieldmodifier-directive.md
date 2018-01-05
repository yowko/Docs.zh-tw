---
title: "x:FieldModifier 指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ed50dd2aff1702543789f06939f7c2bc4b3dd83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier 指示詞
修改 XAML 編譯行為，使具名的物件參考的欄位會定義使用<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>存取而不是<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>預設行為。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*Public*|您將傳遞至指定的完整字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>與<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>會有所差異，使用程式碼後置程式設計語言而定。 請參閱＜備註＞。|  
  
## <a name="dependencies"></a>相依性  
 如果 XAML 生產使用`x:FieldModifier`該 XAML 生產的根項目必須宣告的任何地方、 [X:class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)。  
  
## <a name="remarks"></a>備註  
 `x:FieldModifier`不相關的宣告類別或其成員的一般存取層級。 這樣做只適用於 XAML 處理行為屬於 XAML 生產的特定 XAML 物件處理時，就會變成應用程式的物件圖形中可能可以存取的物件。 根據預設，這類物件的欄位參考會保留私用，它可防止控制項的取用者直接修改的物件圖形。 相反地，控制取用者應該使用標準模式所啟用的程式設計模型，例如藉由取得的版面配置根目錄中，子元素的集合，專用的公用屬性，來修改物件圖形，並以此類推。  
  
 值`x:FieldModifier`屬性會因程式設計語言，與特定架構可以改變其用途。 要使用的字串取決於各種語言的實作方式其<xref:System.CodeDom.Compiler.CodeDomProvider>和類型轉換器，它會傳回定義意義<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>和<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>，以及該語言是否區分大小寫。  
  
-   如[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>是`public`。  
  
-   如[!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]，要傳遞至指定的字串<xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>是`Public`。  
  
-   如[!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)]，XAML 的任何目標目前存在; 因此，要傳遞的字串是未定義。  
  
 您也可以指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>(`internal`中[!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)]，`Friend`中[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) 但指定<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是常見的事因為`NotPublic`時已經是預設行為。  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>是預設行為，因為它不頻繁編譯 XAML 的組件外部的程式碼需要存取 XAML 建立的項目。 WPF 安全性架構，連同 XAML 編譯行為將會宣告為公用，儲存項目執行個體的欄位，除非您特別設定`x:FieldModifier`為允許公用存取。  
  
 `x:FieldModifier`只會與相關的項目[X:name 指示詞](../../../docs/framework/xaml-services/x-name-directive.md)因為該名稱用來參考的欄位之後，它是公用。  
  
 根據預設，部分類別的根項目是公用的。不過，您可以將非公用使用[X:classmodifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)。 [X:classmodifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)也會影響根項目類別的執行個體的存取層級。 您可以將兩者`x:Name`和`x:FieldModifier`根項目，但這只會公用欄位複製的根項目，則為 true 的根項目類別存取層級仍受[X:classmodifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)。  
  
## <a name="see-also"></a>請參閱  
 [WPF 的 XAML 和自訂類別](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [WPF 中的程式碼後置和 XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:Name 指示詞](../../../docs/framework/xaml-services/x-name-directive.md)  
 [建置 WPF 應用程式 (WPF)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [x:ClassModifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
