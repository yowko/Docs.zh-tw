---
title: "Rapid Application Development with My.Resources and My.Settings (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Settings object, developing applications"
  - "rapid application development (RAD), My.Resources"
  - "rapid application development (RAD), My.Settings"
  - "My.Resources object, developing applications"
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: 6
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 6
---
# Rapid Application Development with My.Resources and My.Settings (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`My.Resources` 物件會提供對應用程式資源的存取，並讓您能動態擷取應用程式的資源。  
  
## 擷取資源  
 您可以透過 `My.Resources` 物件擷取一些資源，例如音訊檔案、圖示、影像和字串。  例如，您可以存取應用程式的特定文化特性資源檔。  下列範例會將表單的圖示設為應用程式資源檔中所儲存的圖示 \(名為 `Form1Icon`\)。  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources` 物件只會公開 \(Expose\) 全域資源。  它不會提供與表單相關之資源檔的存取。  您必須從表單存取表單資源。  如需詳細資訊，請參閱[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)。  
  
 同樣地，`My.Settings` 物件會提供應用程式設定的存取，並且可以讓您動態地儲存和擷取應用程式的屬性設定和其他資訊。  如需詳細資訊，請參閱 [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) 和 [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)。  
  
## 請參閱  
 [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)   
 [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Accessing Application Settings](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)