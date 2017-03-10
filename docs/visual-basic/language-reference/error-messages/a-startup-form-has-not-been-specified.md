---
title: "A startup form has not been specified | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_NoStartupForm"
dev_langs: 
  - "VB"
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# A startup form has not been specified
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

應用程式會使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別，但未指定啟動表單。  
  
 如果在專案設計工具中選取了 \[**啟用應用程式架構**\] 核取方塊，但未指定 \[**啟動表單**\]，就可能發生這個錯誤。  如需詳細資訊，請參閱 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)。  
  
### 若要更正這個錯誤  
  
1.  指定應用程式的啟始物件。  
  
     如需詳細資訊，請參閱 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)。  
  
2.  覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> 方法，將 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> 屬性設為啟動表單。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>   
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)