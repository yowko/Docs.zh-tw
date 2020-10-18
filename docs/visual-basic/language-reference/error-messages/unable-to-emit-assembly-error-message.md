---
title: '無法發出組件: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: c088f273c100b1a7eefcf74047865093f378e970
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161656"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a><span data-ttu-id="ca60a-102">BC30145：無法發出元件： \<error message></span><span class="sxs-lookup"><span data-stu-id="ca60a-102">BC30145: Unable to emit assembly: \<error message></span></span>

<span data-ttu-id="ca60a-103">Visual Basic 編譯器會呼叫元件連結器 (*Al.exe*（也稱為 Alink) ）來產生具有資訊清單的元件，而連結器會在建立元件的發出階段中報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca60a-103">The Visual Basic compiler calls the Assembly Linker (*Al.exe*, also known as Alink) to generate an assembly with a manifest, and the linker reports an error in the emission stage of creating the assembly.</span></span>

<span data-ttu-id="ca60a-104">**錯誤識別碼：** BC30145</span><span class="sxs-lookup"><span data-stu-id="ca60a-104">**Error ID:** BC30145</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ca60a-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ca60a-105">To correct this error</span></span>

1. <span data-ttu-id="ca60a-106">查看引號的錯誤訊息，並參閱 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 的主題，以取得進一步的說明和建議。</span><span class="sxs-lookup"><span data-stu-id="ca60a-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) for further explanation and advice.</span></span>

2. <span data-ttu-id="ca60a-107">請嘗試手動簽署元件，方法是使用 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) 或 [Sn.exe (強式名稱工具) ](../../../framework/tools/sn-exe-strong-name-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="ca60a-107">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>

3. <span data-ttu-id="ca60a-108">如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="ca60a-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="ca60a-109">手動簽署組件</span><span class="sxs-lookup"><span data-stu-id="ca60a-109">To sign the assembly manually</span></span>

1. <span data-ttu-id="ca60a-110">使用 [Sn.exe (強式名稱工具) ](../../../framework/tools/sn-exe-strong-name-tool.md)) 建立公開/私密金鑰組檔。</span><span class="sxs-lookup"><span data-stu-id="ca60a-110">Use the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>

   <span data-ttu-id="ca60a-111">這個檔案的副檔名為 *.snk* 。</span><span class="sxs-lookup"><span data-stu-id="ca60a-111">This file has an *.snk* extension.</span></span>

2. <span data-ttu-id="ca60a-112">從專案刪除產生錯誤的 COM 參考。</span><span class="sxs-lookup"><span data-stu-id="ca60a-112">Delete the COM reference that is generating the error from your project.</span></span>

3. <span data-ttu-id="ca60a-113">開啟 [Visual Studio 的開發人員命令提示字元](../../../framework/tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="ca60a-113">Open the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).</span></span>

   <span data-ttu-id="ca60a-114">在 Windows 10 中，于工作列上的搜尋方塊中輸入 **開發人員命令提示** 字元。</span><span class="sxs-lookup"><span data-stu-id="ca60a-114">In Windows 10, enter **Developer command prompt** into the search box on the task bar.</span></span> <span data-ttu-id="ca60a-115">然後，從結果清單中選取 [ **VS 2017 開發人員命令提示字元** ]。</span><span class="sxs-lookup"><span data-stu-id="ca60a-115">Then, select **Developer Command Prompt for VS 2017** from the results list.</span></span>

4. <span data-ttu-id="ca60a-116">將目錄變更為您要放置元件包裝函式的目錄。</span><span class="sxs-lookup"><span data-stu-id="ca60a-116">Change the directory to the directory where you want to place your assembly wrapper.</span></span>

5. <span data-ttu-id="ca60a-117">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ca60a-117">Enter the following command:</span></span>

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   <span data-ttu-id="ca60a-118">您可以輸入的實際命令範例如下：</span><span class="sxs-lookup"><span data-stu-id="ca60a-118">An example of the actual command you might enter is:</span></span>

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > <span data-ttu-id="ca60a-119">如果路徑或檔案包含空格，請使用雙引號。</span><span class="sxs-lookup"><span data-stu-id="ca60a-119">Use double quotation marks if a path or file contains spaces.</span></span>

6. <span data-ttu-id="ca60a-120">在 Visual Studio 中，將 .NET 元件參考新增至您剛才建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="ca60a-120">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca60a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca60a-121">See also</span></span>

- [<span data-ttu-id="ca60a-122">Al.exe</span><span class="sxs-lookup"><span data-stu-id="ca60a-122">Al.exe</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="ca60a-123">Sn.exe (強式名稱工具) </span><span class="sxs-lookup"><span data-stu-id="ca60a-123">Sn.exe (Strong Name Tool)</span></span>](../../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="ca60a-124">如何：建立 Public-Private 金鑰組</span><span class="sxs-lookup"><span data-stu-id="ca60a-124">How to: Create a Public-Private Key Pair</span></span>](../../../standard/assembly/create-public-private-key-pair.md)
- [<span data-ttu-id="ca60a-125">與我們交談</span><span class="sxs-lookup"><span data-stu-id="ca60a-125">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
