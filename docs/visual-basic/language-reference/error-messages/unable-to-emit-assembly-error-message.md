---
title: "無法發出組件：&lt;錯誤訊息&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="51a34-102">無法發出組件：&lt;錯誤訊息&gt;</span><span class="sxs-lookup"><span data-stu-id="51a34-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="51a34-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink) 使用資訊清單產生組件，連結器在建立組件的發出階段回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="51a34-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="51a34-104">**錯誤 ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="51a34-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51a34-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="51a34-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="51a34-106">請檢查引用的錯誤訊息，並參考 [Al.exe 工具錯誤和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) 的主題，以取得進一步說明和建議。</span><span class="sxs-lookup"><span data-stu-id="51a34-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="51a34-107">再試一次 簽署組件以手動方式，使用[Al.exe （組件連結器）](https://msdn.microsoft.com/library/c405shex)或[Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23)。</span><span class="sxs-lookup"><span data-stu-id="51a34-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="51a34-108">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="51a34-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="51a34-109">手動簽署組件</span><span class="sxs-lookup"><span data-stu-id="51a34-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="51a34-110">使用[Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23)建立公開/私密金鑰組檔案。</span><span class="sxs-lookup"><span data-stu-id="51a34-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="51a34-111">這個檔案的副檔名為 .snk。</span><span class="sxs-lookup"><span data-stu-id="51a34-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="51a34-112">從專案刪除產生錯誤的 COM 參考。</span><span class="sxs-lookup"><span data-stu-id="51a34-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="51a34-113">從 Windows**啟動**功能表上，指向**程式**，指向  **Microsoft Visual Studio 2008**，指向  **Visual Studio Tools**，和然後按一下  **Visual Studio 2008 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="51a34-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="51a34-114">移到您要放置組件包裝函式的目錄。</span><span class="sxs-lookup"><span data-stu-id="51a34-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="51a34-115">輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="51a34-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="51a34-116">您可能輸入的程式碼範例如下。</span><span class="sxs-lookup"><span data-stu-id="51a34-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="51a34-117">如果路徑或檔案包含空格，請使用雙引號 (")。</span><span class="sxs-lookup"><span data-stu-id="51a34-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="51a34-118">在 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 中，加入您剛建立之檔案的 .NET Assembly 參考。</span><span class="sxs-lookup"><span data-stu-id="51a34-118">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a34-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51a34-119">See Also</span></span>  
 [<span data-ttu-id="51a34-120">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="51a34-120">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="51a34-121">Al.exe 工具錯誤和警告</span><span class="sxs-lookup"><span data-stu-id="51a34-121">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="51a34-122">Sn.exe (強式名稱工具)</span><span class="sxs-lookup"><span data-stu-id="51a34-122">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="51a34-123">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="51a34-123">How to: Create a Public-Private Key Pair</span></span>](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [<span data-ttu-id="51a34-124">告訴我們</span><span class="sxs-lookup"><span data-stu-id="51a34-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
