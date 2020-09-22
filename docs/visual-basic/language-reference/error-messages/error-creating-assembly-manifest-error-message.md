---
title: '建立組件資訊清單時發生錯誤: <error message>'
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: e90ad1905123a3c5426ada15e21179abe5c078ab
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874410"
---
# <a name="error-creating-assembly-manifest-error-message"></a><span data-ttu-id="6a3ef-102">建立組件資訊清單時發生錯誤: \<error message></span><span class="sxs-lookup"><span data-stu-id="6a3ef-102">Error creating assembly manifest: \<error message></span></span>

<span data-ttu-id="6a3ef-103">Visual Basic 編譯器會呼叫元件連結器 ( # A0，也稱為 Alink) 來產生具有資訊清單的元件。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="6a3ef-104">連結器在建立組件的前置發出階段回報了錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="6a3ef-105">如果指定的金鑰檔或金鑰容器有問題，便可能發生此情形。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="6a3ef-106">若要完全簽署組件，您必須提供有效的金鑰檔，其中包含公開和私密金鑰的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="6a3ef-107">若要延遲簽署組件，您必須選取 [僅延遲簽署]\*\*\*\* 核取方塊，並提供有效的金鑰檔，其中包含公開金鑰資訊的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="6a3ef-108">延遲簽署組件時不需要私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="6a3ef-109">如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../standard/assembly/sign-strong-name.md).</span></span>  
  
 <span data-ttu-id="6a3ef-110">**錯誤識別碼：** BC30140</span><span class="sxs-lookup"><span data-stu-id="6a3ef-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a3ef-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6a3ef-111">To correct this error</span></span>  
  
1. <span data-ttu-id="6a3ef-112">檢查引號的錯誤訊息，並參閱 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)的主題。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="6a3ef-113">針對錯誤 AL1019 進一步說明和建議</span><span class="sxs-lookup"><span data-stu-id="6a3ef-113">for error AL1019 further explanation and advice</span></span>  
  
2. <span data-ttu-id="6a3ef-114">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="6a3ef-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a3ef-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a3ef-115">See also</span></span>

- [<span data-ttu-id="6a3ef-116">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="6a3ef-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="6a3ef-117">專案設計工具、簽署頁</span><span class="sxs-lookup"><span data-stu-id="6a3ef-117">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
- [<span data-ttu-id="6a3ef-118">Al.exe</span><span class="sxs-lookup"><span data-stu-id="6a3ef-118">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="6a3ef-119">與我們交談</span><span class="sxs-lookup"><span data-stu-id="6a3ef-119">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
