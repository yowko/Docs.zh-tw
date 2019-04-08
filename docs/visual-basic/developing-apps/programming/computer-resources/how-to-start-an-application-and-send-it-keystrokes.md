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
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="0da80-102">作法：啟動應用程式並將按鍵輸入傳送至該應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0da80-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="0da80-103">這個範例會使用 `Shell` 函式來啟動小算盤應用程式，然後使用 `My.Computer.Keyboard.SendKeys` 方法來傳送按鍵輸入，以將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="0da80-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0da80-104">範例</span><span class="sxs-lookup"><span data-stu-id="0da80-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0da80-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="0da80-105">Robust Programming</span></span>  
 <span data-ttu-id="0da80-106">如果找不到具有所要求處理序識別碼的應用程式，則會引發 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0da80-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0da80-107">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="0da80-107">.NET Framework Security</span></span>  
 <span data-ttu-id="0da80-108">呼叫 `Shell` 函式需要完全信任 (<xref:System.Security.SecurityException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="0da80-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da80-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0da80-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
