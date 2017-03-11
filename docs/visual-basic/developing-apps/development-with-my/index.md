---
title: "Development with My (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.MyWpfExtension.Windows"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My object"
  - "My namespace"
  - "My feature"
  - "Visual Basic, programming in"
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Development with My (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 會提供快速應用程式開發 \(Rapid Application Development，RAD\) 的新功能，可改進生產力，並提供強大威力，但是仍能保持簡單易用。  其中一項功能 \(名為 `My`\) 會提供應用程式及它執行階段環境之相關資訊和預設物件執行個體的存取。  這項資訊使用 IntelliSense 可探索的格式來組織，並且根據用途分類。  
  
 `My` 的最上層成員會公開 \(Expose\) 為物件。  每個物件的行為與具有 `Shared` 成員的命名空間 \(Namespace\) 或類別 \(Class\) 類似，它還會公開一組相關成員。  
  
 此表會顯示最上層 `My` 物件和彼此之間的關係。  
  
 ![My 的物件模型](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.png "MyObjModel")  
  
## 在本節中  
 [Performing Tasks with My.Application, My.Computer, and My.User](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 描述三個主要的 `My` 物件 \(`My.Application`、`My.Computer` 和 `My.User`\)，它們可以提供對資訊和功能的存取。  
  
 [Default Object Instances Provided by My.Forms and My.WebServices](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 描述 `My.Forms` 和 `My.WebServices` 物件，它們可以提供對應用程式會用到之表單、資料來源和 XML Web Service 的存取。  
  
 [Rapid Application Development with My.Resources and My.Settings](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 描述 `My.Resources` 和 `My.Settings` 物件，它們可以提供對應用程式之資源和設定的存取。  
  
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 描述 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 應用程式啟動\/關閉模型。  
  
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 提供不同專案類型上可用之 `My` 功能的詳細資訊。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)