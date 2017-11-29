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
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="fab60-102">建立組件資訊清單時發生錯誤：&lt;錯誤訊息&gt;</span><span class="sxs-lookup"><span data-stu-id="fab60-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="fab60-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink) 使用資訊清單產生組件。</span><span class="sxs-lookup"><span data-stu-id="fab60-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="fab60-104">連結器在建立組件的前置發出階段回報了錯誤。</span><span class="sxs-lookup"><span data-stu-id="fab60-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="fab60-105">如果指定的金鑰檔或金鑰容器有問題，便可能發生此情形。</span><span class="sxs-lookup"><span data-stu-id="fab60-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="fab60-106">若要完全簽署組件，您必須提供有效的金鑰檔，其中包含公開和私密金鑰的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fab60-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="fab60-107">若要延遲簽署組件，您必須選取 [僅延遲簽署] 核取方塊，並提供有效的金鑰檔，其中包含公開金鑰資訊的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fab60-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="fab60-108">延遲簽署組件時不需要私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="fab60-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="fab60-109">如需詳細資訊，請參閱[如何： 簽署組件 (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)。</span><span class="sxs-lookup"><span data-stu-id="fab60-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="fab60-110">**錯誤 ID:** BC30140</span><span class="sxs-lookup"><span data-stu-id="fab60-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fab60-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="fab60-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="fab60-112">請檢查引用的錯誤訊息，請參閱主題[Al.exe 工具錯誤和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)AL1019 錯誤的進一步說明和建議</span><span class="sxs-lookup"><span data-stu-id="fab60-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="fab60-113">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="fab60-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab60-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fab60-114">See Also</span></span>  
 [<span data-ttu-id="fab60-115">如何：簽署組件 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="fab60-115">How to: Sign an Assembly (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [<span data-ttu-id="fab60-116">專案設計工具、簽署頁面</span><span class="sxs-lookup"><span data-stu-id="fab60-116">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)  
 [<span data-ttu-id="fab60-117">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="fab60-117">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="fab60-118">Al.exe 工具錯誤和警告</span><span class="sxs-lookup"><span data-stu-id="fab60-118">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="fab60-119">告訴我們</span><span class="sxs-lookup"><span data-stu-id="fab60-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
