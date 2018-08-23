---
title: '無法發出組件: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 404a8255adcdc414a40b40395ada1c90c1078325
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754063"
---
# <a name="unable-to-emit-assembly-error-message"></a><span data-ttu-id="53677-102">無法發出組件：\<錯誤訊息 ></span><span class="sxs-lookup"><span data-stu-id="53677-102">Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="53677-103">Visual Basic 編譯器呼叫組件連結器 (*Al.exe*，也稱為 Alink) 來產生組件資訊清單和連結器會在建立組件的發出階段回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="53677-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="53677-104">**錯誤 ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="53677-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="53677-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="53677-105">To correct this error</span></span>

1. <span data-ttu-id="53677-106">檢查引用的錯誤訊息，並參考主題[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)取得進一步說明和建議。</span><span class="sxs-lookup"><span data-stu-id="53677-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="53677-107">嘗試簽署組件以手動的方式，使用[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)或[Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="53677-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="53677-108">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="53677-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="53677-109">手動簽署組件</span><span class="sxs-lookup"><span data-stu-id="53677-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="53677-110">使用  [Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)) 來建立公開/私密金鑰組檔案。</span><span class="sxs-lookup"><span data-stu-id="53677-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="53677-111">此檔案具有 *.snk*延伸模組。</span><span class="sxs-lookup"><span data-stu-id="53677-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="53677-112">從專案刪除產生錯誤的 COM 參考。</span><span class="sxs-lookup"><span data-stu-id="53677-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="53677-113">開啟[Visual Studio 的開發人員命令提示字元](../../../framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="53677-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="53677-114">在 Windows 10 中，輸入**開發人員命令提示字元**在工作列上的搜尋 方塊。</span><span class="sxs-lookup"><span data-stu-id="53677-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="53677-115">然後，選取**適用於 VS 2017 開發人員命令提示字元**從結果清單中。</span><span class="sxs-lookup"><span data-stu-id="53677-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="53677-116">將目錄變更至您要在其中放置您的組件包裝函式的目錄。</span><span class="sxs-lookup"><span data-stu-id="53677-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="53677-117">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="53677-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="53677-118">您可以輸入實際命令的範例是：</span><span class="sxs-lookup"><span data-stu-id="53677-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="53677-119">如果路徑或檔案包含空格，請使用雙引號。</span><span class="sxs-lookup"><span data-stu-id="53677-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="53677-120">在 Visual Studio 中，加入.NET 組件參考，您剛剛建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="53677-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="53677-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53677-121">See also</span></span>

- <span data-ttu-id="53677-122">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="53677-122">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>
- <span data-ttu-id="53677-123">[Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="53677-123">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
- [<span data-ttu-id="53677-124">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="53677-124">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="53677-125">告訴我們</span><span class="sxs-lookup"><span data-stu-id="53677-125">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)