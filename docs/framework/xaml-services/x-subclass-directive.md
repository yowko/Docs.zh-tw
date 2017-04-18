---
title: "x:Subclass Directive | Microsoft Docs"
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
  - "Subclass"
  - "xSubclass"
  - "x:Subclass"
helpviewer_keywords: 
  - "x:Subclass attribute [XAML Services]"
  - "XAML [XAML Services], x:Subclass attribute"
  - "Subclass attribute in XAML [XAML Services]"
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: 20
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 20
---
# x:Subclass Directive
修改同時提供 `x:Class` 時的XAML 標記編譯行為。  不是建立以 `x:Class` 為基底的部分類別，而是將提供的 `x:Class` 建立成中繼類別，然後您的衍生類別就應該以 `x:Class` 為基底來提供。  
  
## XAML Attribute Usage  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## XAML 值  
  
|||  
|-|-|  
|`namespace`|選擇項。  指定包含 `classname` 的 CLR 命名空間。  如果指定了 `namespace`，點 \(.\) 就會分隔 `namespace` 與 `classname`。|  
|`classname`|必要項。  所指定的部分類別 CLR 名稱會連接載入的 XAML 和該 XAML 的程式碼後置。  請參閱＜備註＞。|  
|`subclassNamespace`|選擇項。  如果每個命名空間都能彼此解析，就可能與 `namespace` 不同。  指定包含 `subclassName` 的 CLR 命名空間。  如果指定了 `subclassName`，點 \(.\) 就會分隔 `subclassNamespace` 與 `subclassName`。|  
|`subclassName`|必要項。  指定子類別的 CLR 名稱。|  
  
## 相依性  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) 也必須提供在相同的物件上提供，而且該物件必須是 XAML 產物的根項目。  
  
## 備註  
 `x:Subclass` 的使用方式主要適用於不支援部分類別宣告的語言。  
  
 用來做為 `x:Subclass` 的類別不可以是巢狀類別，而且 `x:Subclass` 必須參考如＜相依性＞一節中所說明的根物件。  
  
 否則 .NET Framework XAML 服務實作並未定義 `x:Subclass` 的概念意義。  這是因為 .NET Framework XAML Services 行為沒有指定 XAML 標記和支援程式碼藉以連接的整體程式設計模型。  與 `x:Class` 和 `x:Subclass` 相關之進一步概念的實作，會由使用程式設計模型或應用程式模型來定義連接 XAML 標記、已編譯標記和 CLR 架構程式碼後置之方式的特定架構來執行。  每個架構都可能有自己的建置動作，可以啟用某些行為，或者是必須包含在建置環境中的特定元件。  在架構內，建置動作也會根據在程式碼後置使用的特定 CLR 語言而有所不同。  
  
## WPF 使用注意事項  
 `x:Subclass` 可以是在頁面根之上，或是在應用程式定義中的 <xref:System.Windows.Application> 根上，該目錄已經具有 `x:Class`。  在頁面或應用程式根項目以外的其他任何項目上宣告 `x:Subclass` ，或是在沒有 `x:Class` 的位置指定它，都會產生編譯時期錯誤。  
  
 建立可針對 `x:Subclass` 案例正確運作的衍生類別相當複雜。  您可能需要檢查中繼檔案 \(透過標記編譯，在您專案的 obj 資料夾中產生的 .g 檔案，其名稱包含 .xaml 檔案名稱\)。  這些中繼檔案可以幫助您在編譯應用程式中已聯結的部分類別中，判斷特定程式設計建構的來源。  
  
 衍生類別中的事件處理常式必須是 `internal override` \([!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] 中的 `Friend Overrides`\)，才能覆寫編譯期間在中繼類別中建立之處理常式的 Stub。  否則衍生類別實作會隱藏 \(遮蔽\) 中繼類別實作，而且不會叫用中繼類別處理常式。  
  
 定義 `x:Class` 和 `x:Subclass` 時，您不需要提供 `x:Class` 所參考之類別的任何實作。  您只需要透過 `x:Class` 屬性 \(Attribute\) 指定其名稱，讓編譯器具有某些指引，可用於它在中繼檔案中建立的類別 \(在這種情況下，編譯器不會選取預設名稱\)。  您可為 `x:Class` 類別提供實作，但這不是同時使用 `x:Class` 和 `x:Subclass` 的一般情節。  
  
## 請參閱  
 [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md)   
 [WPF 的 XAML 和自訂類別](../../../ocs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)