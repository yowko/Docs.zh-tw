---
title: "x:Class Directive | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "x:Class"
  - "xClass"
  - "Class"
helpviewer_keywords: 
  - "Class attribute in XAML [XAML Services]"
  - "XAML [XAML Services], x:Class attribute"
  - "x:Class attribute [XAML Services]"
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 26
---
# x:Class Directive
設定 XAML 標記編譯，以便在標記和程式碼後置之間聯結部分類別。  程式碼部分類別是使用 [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] 語言在另一個程式碼檔案中定義的，而標記的部分類別則通常是在 XAML 編譯期間以程式碼產生方式建立。  
  
## XAML Attribute Usage  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`namespace`|選擇項。  所指定的 [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] 命名空間包含以 `classname` 識別的部分類別。  如果指定了 `namespace`，點 \(.\) 就會分隔 `namespace` 與 `classname`。  請參閱＜備註＞。|  
|`classname`|必要項。  所指定的部分類別 [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] 名稱會連接載入的 XAML 和該 XAML 的程式碼後置。|  
  
## 相依性  
 `x:Class` 只可以在 XAML 產物的根項目上指定。  `x:Class` 在 XAML 產物中具有父代的任何物件上都是無效的。  如需詳細資訊，請參閱 [\[MS\-XAML\] 4.3.1.6 章](http://go.microsoft.com/fwlink/?LinkId=114525) \(英文\)。  
  
## 備註  
 `namespace` 值可能包含額外的點，將相關的命名空間組織成名稱階層架構，這是 .NET Framework 程式設計中的常見技巧。  只有 `x:Class` 值的字串的最後一點會被解譯為個別的`namespace`和`classname.` 。當成`x:Class`使用的類別不可以是巢狀類別。  不允許巢狀類別，因為如果允許巢狀類別，`x:Class` 字串之點的意義會難以判斷。  
  
 在使用 `x:Class` 的現有程式設計模型中，從具有不含任何程式碼後置的 XAML 頁面完全有效的意義上說，`x:Class` 是選擇性的。  不過，該功能會依照使用 XAML 之架構的實作，與建置動作進行互動。  `x:Class` 功能也受到各種 XAML 指定內容分類在應用程式模型及對應建置動作中的角色影響。  如果 XAML 宣告事件處理屬性 \(Attribute\) 值，或是具現化自訂項目，其中定義的類別位於程式碼後置類別中，則必須將 `x:Class` 指示詞參考 \(或 [x:Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)\) 提供給程式碼後置的適當類別。  
  
 `x:Class` 指示詞的值必須是指定類別完整名稱的字串，但是不包括任何組件資訊 \(相當於 <xref:System.Type.FullName%2A?displayProperty=fullName>\)。  對於簡單的應用程式，您可以省略 CLR 命名空間資訊，如果這也是程式碼後置的結構形式即可 \(程式碼定義從類別層級開始\)。  
  
 頁面或應用程式定義的程式碼後置檔案的程式碼檔案，都必須包含為產生編譯應用程式及牽涉標記編譯之專案的一部分。  您必須遵守 CLR 類別的命名規則。  如需詳細資訊，請參閱 [Framework 設計方針](../../../ml/index.xml)。  根據預設，程式碼後置類別必須是 `public`，但可以使用 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)定義成不同的存取層級。  
  
 `x:Class` 屬性的這項解譯僅適用於 CLR 架構的 XAML 實作，尤其是 .NET Framework XAML 服務。  不以 CLR 為基礎，而且不使用 .NET Framework XAML Services 的其他 XAML 實作，可能會使用不同的解析公式來連接 XAML 標記和支援執行階段程式碼。  如需 `x:Class` 之更為一般解譯的詳細資訊，請參閱 [\[MS\-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525) \(英文\)。  
  
 在架構的特定層級，`x:Class` 的意義沒有在 .NET Framework XAML Services 中定義。  這是因為 .NET Framework XAML Services 沒有指定 XAML 標記和支援程式碼藉以連接的程式撰寫模型。  `x:Class` 指示詞的其他用途可能會由使用程式設計模型或應用程式模型定義連接 XAML 標記和 CLR 架構程式碼後置之方式的特定架構來實作。  每個架構都可以有自己的建置動作，可以啟用某些行為，或者是必須包含在建置環境中的特定元件。  在架構內，建置動作也會根據在程式碼後置使用的特定 CLR 語言而有所不同。  
  
## WPF 程式設計模型中的 x:Class  
 在 WPF 應用程式與 WPF 應用程式模型中，`x:Class` 可以宣告做為任何項目的屬性 \(Attribute\)，其中該項目為 XAML 檔案的根項目並且會進行編譯 \(而 XAML 包含在具有 `Page` 建置動作的 WPF 應用程式專案中\)，或是宣告做為已編譯之 WPF 應用程式之應用程式定義中的 <xref:System.Windows.Application> 根項目的屬性。  如果在不是頁面根或應用程式根的項目或尚未編譯的 XAML 檔案宣告 `x:Class`，就會在 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] 和 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] WPF XAML 編譯器之下造成編譯時期錯誤。  如需關於在 WPF 中處理 `x:Class`的其他方面的資訊，請參閱[WPF 中的程式碼後置和 XAML](../../../ocs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)。  
  
## Windows Workflow Foundation 的 x:Class  
 針對 Windows Workflow Foundation，`x:Class` 會命名完全 XAML 組成之自訂活動的類別，或者會命名程式碼後置活動設計工具 XAML 頁面的部份類別。  
  
## Silverlight 使用方式備註  
 Silverlight 的 `x:Class` 會在其他篇幅中做說明。  如需詳細資訊，請參閱[XAML 命名空間 \(x:\) 語言功能 \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## 請參閱  
 [x:Subclass Directive](../../../docs/framework/xaml-services/x-subclass-directive.md)   
 [WPF 的 XAML 和自訂類別](../../../ocs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)   
 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)