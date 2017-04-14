---
title: "如何：在設計階段建立新設定 | Microsoft Docs"
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
  - "應用程式設定 [Windows Form], 建立"
  - "應用程式設定 [Windows Form], 設計階段"
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在設計階段建立新設定
您可以使用 \[設定設計工具\] 在設計階段建立新設定。  \[設定設計工具\] 是格線樣式的介面，可讓您建立新設定並指定這些設定的屬性。  您必須針對這些新設定指定 \[名稱\]、\[值\]、\[類型\] 和 \[範圍\]。  一旦建立設定之後，便可以在程式碼中存取該項設定。  
  
### 若要使用 C\# 在設計階段建立新設定  
  
1.  在 \[**方案總管**\] 中，展開專案的 \[**屬性**\] 節點。  
  
2.  按兩下您要在其中新增設定的 .settings 檔案。  此檔案的預設名稱是 Settings.settings。  
  
3.  在 \[設定設計工具\] 中，針對您的設定來設定 \[名稱\]、\[值\]、\[類型\] 和 \[範圍\]。  每一列都代表單一設定。  
  
### 若要使用 Visual Basic 在設計階段建立新設定  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案節點，然後選擇 \[**屬性**\]。  
  
2.  在 \[**屬性**\] 頁面中，選取 \[**設定**\] 索引標籤。  
  
3.  在 \[設定設計工具\] 中，針對您的設定來設定 \[名稱\]、\[值\]、\[類型\] 和 \[範圍\]。  每一列都代表單一設定。  
  
## 請參閱  
 [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [如何：在設計階段變更現有設定的值](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)