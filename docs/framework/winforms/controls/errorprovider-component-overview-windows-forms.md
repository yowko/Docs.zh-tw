---
title: "ErrorProvider 元件概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ErrorProvider"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "錯誤訊息, 顯示"
  - "ErrorProvider 元件 [Windows Form], 關於 ErrorProvider 元件"
  - "錯誤 [Windows Form], 顯示給使用者"
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ErrorProvider 元件概觀 (Windows Form)
Windows Form [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) 元件用來驗證使用者在表單或控制項中的輸入。  它通常會和使用者的表單輸入驗證一起使用，或在資料集中顯示錯誤。  錯誤提供者是一種比在訊息方塊中顯示錯誤訊息更好的替代方式，因為當訊息方塊關閉後，就看不到錯誤訊息了。  <xref:System.Windows.Forms.ErrorProvider> 元件會在相關的控制項 \(例如文字方塊\) 旁，顯示錯誤圖示 \(![ErrorProvider 圖示](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.png "vbErrorProviderIcon")\)；當使用者將滑鼠指標指向錯誤圖示時，會出現工具提示並顯示錯誤訊息字串。  
  
## 主要屬性  
 <xref:System.Windows.Forms.ErrorProvider> 元件的主要屬性為 <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> 和 <xref:System.Windows.Forms.ErrorProvider.Icon%2A>。  在使用 <xref:System.Windows.Forms.ErrorProvider> 元件和資料繫結控制項時，<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> 屬性必須設定為適當的容器 \(Container\) \(通常是 Windows Form\)，才能讓元件在表單中顯示錯誤圖示。  在設計工具中加入元件後，<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> 屬性會設定為包含表單；如果您在程式碼中加入控制項，就必須自行設定這個屬性。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> 屬性可以設定為自訂的錯誤圖示，而不使用預設圖示。  設定 <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> 屬性後，<xref:System.Windows.Forms.ErrorProvider> 元件就可以顯示資料集的錯誤訊息。  <xref:System.Windows.Forms.ErrorProvider> 元件的主要方法是 <xref:System.Windows.Forms.ErrorProvider.SetError%2A> 方法，用來指定錯誤訊息字串和顯示錯誤圖示的位置。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> 元件不提供可及性用戶端的內建支援。  若要在使用這個元件時，讓您的應用程式變得可存取，您必須提供其他的可存取回應機制。  
  
## 請參閱  
 <xref:System.Windows.Forms.ErrorProvider>   
 [如何：使用 Windows Form ErrorProvider 元件檢視資料集錯誤](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)   
 [如何：使用 Windows Form ErrorProvider 元件顯示表單驗證的錯誤圖示](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)