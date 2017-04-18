---
title: "如何：撰寫 Windows Form 的控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form], 建立"
  - "自訂控制項 [Windows Form], 建立"
  - "UserControl 類別, Windows Form"
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：撰寫 Windows Form 的控制項
控制項代表使用者和程式之間的圖形連結。  控制項可提供或處理資料、接受使用者輸入、回應事件或者執行連接使用者與應用程式的任何數量的其他功能。  由於控制項基本上是含圖形介面的元件，所以可以執行元件可做的任何功能，並提供使用者互動。  控制項的建立是為了服務特定目的，而撰寫控制項只是另一個程式設計工作。  請牢記在心，下列步驟代表控制項撰寫處理序的概觀。  連結提供個別步驟的其他資訊。  
  
> [!NOTE]
>  如果想要編寫自訂控制項以在 Web Form 上使用，請參閱[Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)。  
>   
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要撰寫控制項  
  
1.  在決定控制項要完成哪些工作，或控制項在應用程式什麼樣的角色時，  要考慮的重點有：  
  
    -   您需要哪種圖形介面？  
  
    -   這個控制項要處理的特定使用者互動為何？  
  
    -   有任何的現有控制項提供您所需的功能嗎？  
  
    -   您可以結合多個 Windows Form 控制項來取得所需要的功能嗎？  
  
2.  如果您的控制項需要物件模型 \(Object Model\)，請決定功能要如何散發到整個物件模型，及要如何劃分控制項和任何子物件 \(Subobject\) 之間的功能。  如果您要規劃複雜的控制項，或希望加入多個功能，則物件模型可能會很有用。  
  
3.  決定您所需的控制項類型 \(例如，使用者控制項、自訂控制項和繼承的 Windows Form 控制項\)。  如需詳細資訊，請參閱 [控制項類型建議](../../../../docs/framework/winforms/controls/control-type-recommendations.md) 與 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)。  
  
4.  將功能表示為控制項的屬性、方法和事件，以及子物件或附屬結構，並指派適當的存取層級 \(例如，公用 \(Public\)、保護 \(Protected\) 等等\)。  
  
5.  如果您需要自訂您控制項的繪製，請加入它的程式碼。  如需詳細資訊，請參閱 [自訂控制項繪製和轉譯](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)。  
  
6.  如果控制項是繼承自 <xref:System.Windows.Forms.UserControl>，您就可以透過建置控制項專案並在 \[**使用者測試容器**\] 中執行，以測試執行階段行為。  如需詳細資訊，請參閱 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
7.  您也可以建立新專案 \(例如 Windows 應用程式\) 並將它放置在容器中，藉此測試和偵錯控制項。  [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)中會示範這個處理序。  
  
8.  當您加入每一個功能，請將功能加入您的測試專案以執行新功能。  
  
9. 重複修正設計。  
  
10. 封裝和部署您的控制項。  如需詳細資訊，請參閱[部署應用程式、服務和元件](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)。  
  
## 請參閱  
 [逐步解說：使用 Visual Basic 撰寫複合控制項](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [逐步解說：使用 Visual Basic 繼承自 Windows Form 控制項](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [如何：繼承自 UserControl 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [如何：繼承自 Control 類別](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [如何：繼承自現有的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)   
 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)   
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)