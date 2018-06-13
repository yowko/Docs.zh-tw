---
title: 如何：啟動應用程式並且將按鍵傳送至該應用程式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 716c88153ad01c7b225f31948c8aaaa2694dc512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582144"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="f17d4-102">如何：啟動應用程式並且將按鍵傳送至該應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f17d4-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="f17d4-103">這個範例會使用 `Shell` 函式來啟動小算盤應用程式，然後使用 `My.Computer.Keyboard.SendKeys` 方法來傳送按鍵輸入，以將兩個數字相乘。</span><span class="sxs-lookup"><span data-stu-id="f17d4-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f17d4-104">範例</span><span class="sxs-lookup"><span data-stu-id="f17d4-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="f17d4-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="f17d4-105">Robust Programming</span></span>  
 <span data-ttu-id="f17d4-106">如果找不到具有所要求處理序識別碼的應用程式，則會引發 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f17d4-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f17d4-107">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="f17d4-107">.NET Framework Security</span></span>  
 <span data-ttu-id="f17d4-108">呼叫 `Shell` 函式需要完全信任 (<xref:System.Security.SecurityException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="f17d4-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f17d4-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="f17d4-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
