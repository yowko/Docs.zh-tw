---
title: 如何：啟動應用程式併發送按鍵 - 視覺基礎知識
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
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="6673b-102">如何：啟動應用程式併發送按鍵（可視基本）</span><span class="sxs-lookup"><span data-stu-id="6673b-102">How to: start an application and send it keystrokes (Visual Basic)</span></span>

<span data-ttu-id="6673b-103">本示例使用<xref:Microsoft.VisualBasic.Interaction.Shell%2A>方法啟動記事本應用程式，然後使用[My.Computer.鍵盤.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A)方法發送擊鍵來列印句子。</span><span class="sxs-lookup"><span data-stu-id="6673b-103">This example uses the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> method to start the Notepad application and then prints a sentence by sending keystrokes using the [My.Computer.Keyboard.SendKeys](xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A) method.</span></span>

## <a name="example"></a><span data-ttu-id="6673b-104">範例</span><span class="sxs-lookup"><span data-stu-id="6673b-104">Example</span></span>

[!code-vb[VbVbalrMyComputer#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#25)]

## <a name="robust-programming"></a><span data-ttu-id="6673b-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6673b-105">Robust programming</span></span>

<span data-ttu-id="6673b-106">如果<xref:System.ArgumentException>找不到具有請求的進程識別碼的應用程式，則引發異常。</span><span class="sxs-lookup"><span data-stu-id="6673b-106">An <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6673b-107">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6673b-107">.NET Framework Security</span></span>

<span data-ttu-id="6673b-108">呼叫 `Shell` 函式需要完全信任 (<xref:System.Security.SecurityException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="6673b-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>

## <a name="see-also"></a><span data-ttu-id="6673b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6673b-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>
- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
