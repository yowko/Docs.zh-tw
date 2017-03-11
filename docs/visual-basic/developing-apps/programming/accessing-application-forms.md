---
title: "Accessing Application Forms (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "forms, communicating between"
  - "application forms, accessing"
  - "forms, accessing one from another"
  - "My.Forms object"
  - "forms, accessing all open"
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Accessing Application Forms (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`My.Forms` 物件會提供一個簡便的方式，存取應用程式專案中所宣告之每個 Windows Form 的執行個體。  您也可以使用 `My.Application` 物件的屬性 \(Property\)，存取應用程式的啟動顯示畫面和主要表單，並取得應用程式之開啟表單的清單。  
  
## 工作  
 下表所列的範例會顯示如何存取應用程式表單。  
  
|||  
|-|-|  
|若要|請參閱|  
|從應用程式的其他表單存取某一個表單。|[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|顯示所有應用程式之開啟表單的標題。|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|應用程式啟動時，以狀態資訊更新啟動顯示畫面。|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)