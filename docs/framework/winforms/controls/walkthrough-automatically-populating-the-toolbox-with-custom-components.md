---
title: "逐步解說：自動將自訂元件填入工具箱 | Microsoft Docs"
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
  - "自訂元件, 加入至工具箱"
  - "IToolboxService 介面"
  - "工具箱 [Windows Form], 填入"
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# 逐步解說：自動將自訂元件填入工具箱
如果元件是由目前開啟方案中的專案所定義，您不需進行任何動作，這些元件就會自動出現在 \[**工具箱**\] 中。  您也可以使用 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/bd07835f-18a8-433e-bccc-7141f65263bb)，以手動方式將自訂元件填入 \[**工具箱**\]，但是 \[**工具箱**\] 會使用下列所有特性來考量方案建置輸出中的項目：  
  
-   實作 <xref:System.ComponentModel.IComponent>；  
  
-   並未將 <xref:System.ComponentModel.ToolboxItemAttribute> 設定為 `false`；  
  
-   並未將 <xref:System.ComponentModel.DesignTimeVisibleAttribute> 設定為 `false`。  
  
> [!NOTE]
>  因為 \[**工具箱**\] 沒有遵循參考鏈結，所以不會顯示並非由方案中的專案建置的項目。  
  
 這個逐步解說示範在建置自訂元件後，如何讓此元件自動出現在 \[**工具箱**\] 中。  逐步解說將說明的工作包括：  
  
-   建立 Windows Form 專案  
  
-   建立自訂元件。  
  
-   建立自訂元件的執行個體。  
  
-   卸載和重新載入自訂元件。  
  
 當您完成時，將會看見您所建立的元件填入了 \[**工具箱**\]。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 第一個步驟是建立專案並設定表單。  
  
#### 若要建立專案  
  
1.  建立名為 `ToolboxExample` 的 Windows 架構應用程式專案。  
  
     如需詳細資訊，請參閱 [How to: Create a Windows Application Project](http://msdn.microsoft.com/zh-tw/b2f93fed-c635-4705-8d0e-cf079a264efa)。  
  
2.  加入新的元件至專案。  將它稱為 `DemoComponent`。  
  
     如需詳細資訊，請參閱 [NIB:How to: Add New Project Items](http://msdn.microsoft.com/zh-tw/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)。  
  
3.  建置專案。  
  
4.  按一下 \[**工具**\] 功能表上的 \[**選項**\] 項目。  按一下 \[**Windows Form 設計工具**\] 項目下的 \[**一般**\]，並確定 \[**AutoToolboxPopulate**\] 選項設定為 \[**True**\]。  
  
## 建立自訂元件的執行個體  
 下一步則是建立表單上自訂元件的執行個體。  因為 \[**工具箱**\] 會自動產生新元件，所以這就和建立任何其他元件或控制項一樣簡單。  
  
#### 若要建立自訂元件的執行個體  
  
1.  在 \[**Form 設計工具**\] 中開啟專案的表單。  
  
2.  在 \[**工具箱**\] 中按一下稱為 \[**ToolboxExample 元件**\] 的新索引標籤。  
  
     按一下索引標籤後，您就會看見 \[**DemoComponent**\]。  
  
    > [!NOTE]
    >  基於效能原因，\[**工具箱**\] 自動填入區域的元件不會顯示自訂點陣圖，且不支援 <xref:System.Drawing.ToolboxBitmapAttribute>。  若要在 \[**工具箱**\] 中顯示自訂元件的圖示，請使用 \[**選擇工具箱項目**\] 對話方塊載入您的元件。  
  
3.  將您的元件拖曳至表單上。  
  
     會建立元件的執行個體，並將它加入至 \[**元件匣**\]。  
  
## 卸載和重新載入自訂元件  
 \[**工具箱**\] 會考慮每個載入專案中的元件，且在卸載專案時移除對專案元件的參考。  
  
#### 若要實驗在工具箱上卸載和重新載入元件的作用  
  
1.  將專案從方案中卸載。  
  
     如需卸載專案的詳細資訊，請參閱 [NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/zh-tw/abc0155b-8fcb-4ffc-95b6-698518a7100b)。  如果您接到儲存的提示，請選擇 \[**是**\]。  
  
2.  加入新的 \[**Windows 應用程式**\] 專案至方案。  在 \[**設計工具**\] 中開啟表單。  
  
     來自先前專案的 \[**ToolboxExample 元件**\] 索引標籤已經移走了。  
  
3.  重新載入 \[`ToolboxExample`\] 專案。  
  
     \[**ToolboxExample 元件**\] 索引標籤會再度出現。  
  
## 後續步驟  
 這個逐步解說示範 \[**工具箱**\] 對專案元件的考量，不過 \[**工具箱**\] 也會考慮控制項。  從方案加入或移除控制項專案，藉此試用您的自訂控制項。  
  
## 請參閱  
 [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/zh-tw/8dd170af-72f0-4212-b04b-034ceee92834)   
 [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/zh-tw/21285050-cadd-455a-b1f5-a2289a89c4db)   
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)