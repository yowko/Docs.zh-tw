---
title: "如何：在執行階段使用 C# 讀取設定 | Microsoft Docs"
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
  - "應用程式設定 [Windows Form], 讀取"
  - "應用程式設定 [Windows Form], 執行階段"
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在執行階段使用 C# 讀取設定
您可以在執行階段透過屬性物件來讀取應用程式範圍和使用者範圍的設定。  屬性物件會透過 Properties.Settings.Default 成員公開所有專案的預設值。  
  
### 在執行階段使用 C\# 讀取設定  
  
-   透過 Properties.Settings.Default 成員存取適當的設定。  下列範例示範如何指派名為 `myColor` 的設定給 BackColor 屬性。  它會要求您具有先前建立的設定檔，其中包含 `System.Drawing.Color` 類型之名為 `myColor` 的設定。  如需建立設定檔的詳細資訊，請參閱[如何：在設計階段建立新設定](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)。  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## 請參閱  
 [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [如何：在執行階段使用 C\# 撰寫使用者設定](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)   
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)