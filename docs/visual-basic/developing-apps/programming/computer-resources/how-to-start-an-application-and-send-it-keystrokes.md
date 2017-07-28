---
title: "如何：啟動應用程式並且將按鍵輸入傳送至該應用程式 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 314d62ae0699e63aab2dff25cce2ce37552e2a20
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>如何：啟動應用程式並且將按鍵傳送至該應用程式 (Visual Basic)
這個範例會使用 `Shell` 函式來啟動小算盤應用程式，然後使用 `My.Computer.Keyboard.SendKeys` 方法來傳送按鍵輸入，以將兩個數字相乘。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果找不到具有所要求處理序識別碼的應用程式，則會引發 <xref:System.ArgumentException> 例外狀況。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫 `Shell` 函式需要完全信任 (<xref:System.Security.SecurityException> 類別)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
