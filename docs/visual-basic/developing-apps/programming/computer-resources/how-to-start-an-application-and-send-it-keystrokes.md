---
title: 作法：啟動應用程式並將按鍵輸入傳送至該應用程式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 9519fd85177d5d2adf97b54652c19330954edadf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815962"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>作法：啟動應用程式並將按鍵輸入傳送至該應用程式 (Visual Basic)
這個範例會使用 `Shell` 函式來啟動小算盤應用程式，然後使用 `My.Computer.Keyboard.SendKeys` 方法來傳送按鍵輸入，以將兩個數字相乘。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果找不到具有所要求處理序識別碼的應用程式，則會引發 <xref:System.ArgumentException> 例外狀況。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 呼叫 `Shell` 函式需要完全信任 (<xref:System.Security.SecurityException> 類別)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
