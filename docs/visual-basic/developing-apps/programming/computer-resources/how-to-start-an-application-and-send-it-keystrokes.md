---
title: 如何：啟動應用程式並將按鍵傳送至 Visual Basic
ms.date: 10/23/2019
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 033999c07bb5839a264122b2ca330916bdf844b8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "72919397"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="519ab-102">如何：啟動應用程式並將按鍵傳送（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="519ab-102">How to: start an application and send it keystrokes (Visual Basic)</span></span>

<span data-ttu-id="519ab-103">這個範例會使用<xref:Microsoft.VisualBasic.Interaction.Shell%2A>方法來啟動 [記事本] 應用程式，然後使用 [ [my.user](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) ] 方法傳送按鍵來列印句子。</span><span class="sxs-lookup"><span data-stu-id="519ab-103">This example uses the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> method to start the Notepad application and then prints a sentence by sending keystrokes using the [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) method.</span></span>

## <a name="example"></a><span data-ttu-id="519ab-104">範例</span><span class="sxs-lookup"><span data-stu-id="519ab-104">Example</span></span>

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a><span data-ttu-id="519ab-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="519ab-105">Robust programming</span></span>

<span data-ttu-id="519ab-106">如果<xref:System.ArgumentException>找不到具有所要求進程識別碼的應用程式，就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="519ab-106">An <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="519ab-107">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="519ab-107">.NET Framework Security</span></span>

<span data-ttu-id="519ab-108">呼叫 `Shell` 函式需要完全信任 (<xref:System.Security.SecurityException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="519ab-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="519ab-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="519ab-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
