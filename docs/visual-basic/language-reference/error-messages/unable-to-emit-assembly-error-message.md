---
title: 無法發出組件：&lt;錯誤訊息&gt;
ms.date: 07/20/2015
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 8f497069088ad30a3be58d02caa0a32f7f1b21b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595169"
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="c656e-102">無法發出組件：&lt;錯誤訊息&gt;</span><span class="sxs-lookup"><span data-stu-id="c656e-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="c656e-103">Visual Basic 編譯器呼叫組件連結器 (Al.exe，也稱為 Alink) 產生資訊清單，與組件，連結器在建立組件的發出階段回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="c656e-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="c656e-104">**錯誤 ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="c656e-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c656e-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c656e-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c656e-106">請檢查引用的錯誤訊息，請參閱主題[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="c656e-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="c656e-107">以取得進一步說明和建議。</span><span class="sxs-lookup"><span data-stu-id="c656e-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="c656e-108">再試一次 簽署組件以手動方式，使用[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)或[Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="c656e-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="c656e-109">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="c656e-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="c656e-110">手動簽署組件</span><span class="sxs-lookup"><span data-stu-id="c656e-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="c656e-111">使用 [Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)) 建立公開/私密金鑰組檔案。</span><span class="sxs-lookup"><span data-stu-id="c656e-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="c656e-112">這個檔案的副檔名為 .snk。</span><span class="sxs-lookup"><span data-stu-id="c656e-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="c656e-113">從專案刪除產生錯誤的 COM 參考。</span><span class="sxs-lookup"><span data-stu-id="c656e-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="c656e-114">從 Windows**啟動**功能表上，指向**程式**，指向  **Microsoft Visual Studio 2008**，指向  **Visual Studio Tools**，和然後按一下  **Visual Studio 2008 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="c656e-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="c656e-115">移到您要放置組件包裝函式的目錄。</span><span class="sxs-lookup"><span data-stu-id="c656e-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="c656e-116">輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="c656e-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="c656e-117">您可能輸入的程式碼範例如下。</span><span class="sxs-lookup"><span data-stu-id="c656e-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="c656e-118">如果路徑或檔案包含空格，請使用雙引號 (")。</span><span class="sxs-lookup"><span data-stu-id="c656e-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="c656e-119">在 Visual Studio 中，加入您剛才建立的檔案的.NET 組件參考。</span><span class="sxs-lookup"><span data-stu-id="c656e-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c656e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c656e-120">See Also</span></span>  
 
 <span data-ttu-id="c656e-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="c656e-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="c656e-122">[Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="c656e-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="c656e-123">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="c656e-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="c656e-124">告訴我們</span><span class="sxs-lookup"><span data-stu-id="c656e-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
