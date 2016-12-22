---
title: "Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Application object, developing applications"
  - "rapid application development (RAD), My.Application"
  - "rapid application development (RAD), My.Computer"
  - "rapid application development (RAD), My.User"
  - "My.Computer object, developing applications"
  - "My.User object, developing applications"
ms.assetid: c8af61bd-4dd3-4a0f-9af5-795b594b240b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Performing Tasks with My.Application, My.Computer, and My.User (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

可提供資訊和常用功能之存取的三個核心 `My` 物件是 `My.Application` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>\)、`My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\) 和 `My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\)。  您可以使用這些物件，分別存取與目前應用程式、安裝應用程式之電腦，或應用程式之目前使用者相關的資訊。  
  
## My.Application、My.Computer 和 My.User  
 下列範例將示範如何使用 `My` 擷取資訊。  
  
 [!CODE [VbVbcnMy#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnMy#1)]  
  
 [!CODE [VbVbcnMy#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnMy#2)]  
  
 除了擷取資訊以外，透過這三個物件公開的成員也能讓您執行與該物件相關的方法。  例如，您可以透過 `My.Computer`，存取各種管理檔案或更新登錄的方法。  
  
 透過 `My`，檔案 I\/O 明顯地變得更為容易且速度更快，包括管理檔案、目錄和磁碟的各種方法及屬性。  <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件可讓您從具有分隔或固定寬度欄位的大型結構檔案讀取。  這個範例會開啟 `TextFieldParser` `reader`，並使用它讀取 `C:\TestFolder1\test1.txt`。  
  
 [!code-vb[VbVbalrTextFieldParser#23](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/performing-tasks-with-my-application-my-computer-and-my-user_1.vb)]  
  
 `My.Application` 可讓您變更應用程式的文化特性 \(Culture\)。  下列範例將示範如何呼叫這個方法。  
  
 [!CODE [VbVbcnMy#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnMy#3)]  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)