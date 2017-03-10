---
title: "/nowin32manifest (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/nowin32manifest compiler option [Visual Basic]"
  - "nowin32manifest compiler option [Visual Basic]"
  - "-nowin32manifest compiler option [Visual Basic]"
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# /nowin32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。  
  
## 語法  
  
```  
/nowin32manifest  
```  
  
## 備註  
 使用此選項時，應用程式會受制於 Windows Vista 的虛擬化，除非您在 Win32 資源檔或稍後建置步驟中提供應用程式資訊清單。  如需虛擬化的詳細資訊，請參閱 [Windows Vista 的 ClickOnce 部署](/visual-studio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如需建立資訊清單的詳細資訊，請參閱 [\/win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [應用程式頁面，專案設計工具 \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)