---
title: "建立組件資訊清單時發生錯誤：&lt;錯誤訊息&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e88d28ef787eb57b71d94f4ee51c09e9751dbff
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="7e5c4-102">建立組件資訊清單時發生錯誤：&lt;錯誤訊息&gt;</span><span class="sxs-lookup"><span data-stu-id="7e5c4-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="7e5c4-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink) 使用資訊清單產生組件。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="7e5c4-104">連結器在建立組件的前置發出階段回報了錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="7e5c4-105">如果指定的金鑰檔或金鑰容器有問題，便可能發生此情形。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="7e5c4-106">若要完全簽署組件，您必須提供有效的金鑰檔，其中包含公開和私密金鑰的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="7e5c4-107">若要延遲簽署組件，您必須選取 [僅延遲簽署] 核取方塊，並提供有效的金鑰檔，其中包含公開金鑰資訊的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="7e5c4-108">延遲簽署組件時不需要私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="7e5c4-109">如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="7e5c4-110">**錯誤 ID:** BC30140</span><span class="sxs-lookup"><span data-stu-id="7e5c4-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e5c4-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="7e5c4-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="7e5c4-112">請檢查引用的錯誤訊息，請參閱主題[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="7e5c4-113">以錯誤 AL1019 進一步說明和建議</span><span class="sxs-lookup"><span data-stu-id="7e5c4-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="7e5c4-114">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e5c4-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e5c4-115">See Also</span></span>  
 [<span data-ttu-id="7e5c4-116">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="7e5c4-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="7e5c4-117">專案設計工具、簽署頁面</span><span class="sxs-lookup"><span data-stu-id="7e5c4-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 <span data-ttu-id="7e5c4-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="7e5c4-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="7e5c4-119">告訴我們</span><span class="sxs-lookup"><span data-stu-id="7e5c4-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
