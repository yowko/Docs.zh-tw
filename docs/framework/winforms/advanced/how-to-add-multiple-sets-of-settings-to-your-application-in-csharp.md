---
title: "如何：在 C# 中將多組設定加入至應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "應用程式設定 [Windows Form], C#"
  - "應用程式設定 [Windows Form], 多組"
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：在 C# 中將多組設定加入至應用程式
在某些情況下，您可能想要在應用程式中擁有多組設定。  例如，您正要開發應用程式，其中某一組設定預期會時常變更，如此則建議您將全部的設定分隔到單一檔案，如此一來，便可一次取代整個檔案，其他設定則不受影響。  Visual Studio 可讓您將多組設定加入至專案，  其他組設定則可以透過 Properties.Settings 物件存取。  
  
### 若要將其他組設定加入至您的應用程式  
  
1.  從 \[**專案**\] 功能表選擇 \[**加入新項目**\]。  \[**加入新項目**\] 對話方塊隨即開啟。  
  
2.  在 \[**加入新項目**\] 對話方塊中選取 \[**設定檔**\]，輸入檔案的名稱，然後按一下 \[**加入**\] 將新設定加入至您的方案。  
  
3.  在 \[**方案總管**\] 中，將新的設定檔拖曳到 \[**屬性**\] 資料夾中。  如此一來，就能在程式碼中使用您的新設定。  
  
4.  以您在任何其他設定檔中使用的方式，在此檔案中加入和使用設定。  您可以透過 Properties.Settings 物件存取此組設定。  
  
## 請參閱  
 [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)