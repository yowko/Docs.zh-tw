---
title: "無法發出組件︰&lt;錯誤訊息&gt;|Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
dev_langs:
- VB
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d15981a1a2fb31ba377066fa421f5a9979d47a12
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="02c24-102">無法發出組件︰&lt;錯誤訊息&gt;</span><span class="sxs-lookup"><span data-stu-id="02c24-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="02c24-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink) 使用資訊清單產生組件，連結器在建立組件的發出階段回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="02c24-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="02c24-104">**錯誤識別碼︰** BC30145</span><span class="sxs-lookup"><span data-stu-id="02c24-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02c24-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="02c24-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="02c24-106">檢查引用的錯誤訊息，並參考主題[Al.exe 工具錯誤和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)的進一步說明和建議。</span><span class="sxs-lookup"><span data-stu-id="02c24-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="02c24-107">請嘗試 簽署組件以手動方式，使用[Al.exe （組件連結器）](https://msdn.microsoft.com/library/c405shex)或[Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23)。</span><span class="sxs-lookup"><span data-stu-id="02c24-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="02c24-108">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="02c24-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="02c24-109">手動簽署組件</span><span class="sxs-lookup"><span data-stu-id="02c24-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="02c24-110">使用[Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23)建立公開/私密金鑰組檔案。</span><span class="sxs-lookup"><span data-stu-id="02c24-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="02c24-111">這個檔案的副檔名為 .snk。</span><span class="sxs-lookup"><span data-stu-id="02c24-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="02c24-112">從專案刪除產生錯誤的 COM 參考。</span><span class="sxs-lookup"><span data-stu-id="02c24-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="02c24-113">從 Windows**啟動**功能表上，指向**程式**，指向  **Microsoft Visual Studio 2008**，指向  **Visual Studio Tools**，然後按一下  **Visual Studio 2008 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="02c24-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="02c24-114">移到您要放置組件包裝函式的目錄。</span><span class="sxs-lookup"><span data-stu-id="02c24-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="02c24-115">輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="02c24-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="02c24-116">您可能輸入的程式碼範例如下。</span><span class="sxs-lookup"><span data-stu-id="02c24-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="02c24-117">如果路徑或檔案包含空格，請使用雙引號 (")。</span><span class="sxs-lookup"><span data-stu-id="02c24-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="02c24-118">在 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 中，加入您剛建立之檔案的 .NET Assembly 參考。</span><span class="sxs-lookup"><span data-stu-id="02c24-118">In [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c24-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02c24-119">See Also</span></span>  
 <span data-ttu-id="02c24-120">[Al.exe （組件連結器）](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="02c24-120">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="02c24-121"> [Al.exe 工具錯誤和警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span><span class="sxs-lookup"><span data-stu-id="02c24-121"> [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span></span>  
<span data-ttu-id="02c24-122"> [Sn.exe （強式名稱工具）](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="02c24-122"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="02c24-123"> [如何：建立公開/私密金鑰組](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span><span class="sxs-lookup"><span data-stu-id="02c24-123"> [How to: Create a Public-Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span></span>  
<span data-ttu-id="02c24-124"> [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="02c24-124"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
