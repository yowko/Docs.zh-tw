---
title: 作法：啟動應用程式並將按鍵輸入傳送至該應用程式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: f130429e5b0964dc8680441fb83cb06d45904a69
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966199"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="88441-102">HOW TO：啟動應用程式並將按鍵輸入傳送至該應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88441-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="88441-103">這個範例會使用 `Shell` 函式來啟動小算盤應用程式，然後使用 `My.Computer.Keyboard.SendKeys` 方法來傳送按鍵輸入，以將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="88441-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88441-104">範例</span><span class="sxs-lookup"><span data-stu-id="88441-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="88441-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="88441-105">Robust Programming</span></span>  
 <span data-ttu-id="88441-106">如果找不到具有所要求處理序識別碼的應用程式，則會引發 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="88441-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="88441-107">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="88441-107">.NET Framework Security</span></span>  
 <span data-ttu-id="88441-108">呼叫 `Shell` 函式需要完全信任 (<xref:System.Security.SecurityException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="88441-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88441-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88441-109">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
