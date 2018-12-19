---
title: HOW TO：為 Visual Studio 命令列設定環境變數
ms.date: 09/29/2017
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: 3563f668dfd4610e1c5cd7d7f8633943c654f193
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286438"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="e4c74-102">HOW TO：為 Visual Studio 命令列設定環境變數</span><span class="sxs-lookup"><span data-stu-id="e4c74-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="e4c74-103">VsDevCmd.bat 檔案可設定適當的環境變數，以啟用命令列組建。</span><span class="sxs-lookup"><span data-stu-id="e4c74-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="e4c74-104">VsDevCmd.bat 檔是隨附於 Visual Studio 2017 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="e4c74-104">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="e4c74-105">Visual Studio 2015 及更早的版本則使用 VSVARS32.bat 作為相同用途。</span><span class="sxs-lookup"><span data-stu-id="e4c74-105">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="e4c74-106">此檔案的儲存位置為 \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools。</span><span class="sxs-lookup"><span data-stu-id="e4c74-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="e4c74-107">如果安裝最新版 Visual Studio 的電腦上也有安裝舊版 Visual Studio，請勿於相同的命令提示字元視窗中，執行不同版本的 VsDevCmd.bat 及 VSVARS32.BAT。</span><span class="sxs-lookup"><span data-stu-id="e4c74-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="e4c74-108">而是應改為在各版本本身的視窗中執行命令。</span><span class="sxs-lookup"><span data-stu-id="e4c74-108">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="e4c74-109">執行 VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="e4c74-109">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="e4c74-110">從 [開始] 功能表中，開啟 [適用於 VS 2017 的開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="e4c74-110">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="e4c74-111">位置在 **Visual Studio 2017** 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e4c74-111">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="e4c74-112">根據您的安裝變更到 \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools 或是 \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools 子目錄。</span><span class="sxs-lookup"><span data-stu-id="e4c74-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="e4c74-113">(目前的*版本*為 *2017*。</span><span class="sxs-lookup"><span data-stu-id="e4c74-113">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="e4c74-114">*供應項目*為 *Enterprise*、*Professional* 或 *Community* 中的其中一個。)</span><span class="sxs-lookup"><span data-stu-id="e4c74-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="e4c74-115">鍵入 **VsDevCmd**以執行 VsDevCmd.bat。</span><span class="sxs-lookup"><span data-stu-id="e4c74-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="e4c74-116">在不同的電腦上，VsDevCmd.bat 檔案可能也不同。</span><span class="sxs-lookup"><span data-stu-id="e4c74-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="e4c74-117">請勿使用另一部電腦的 VsDevCmd.bat 來取代遺失或損毀的 VsDevCmd.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="e4c74-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="e4c74-118">請重新執行安裝程式以取代遺失的檔案。</span><span class="sxs-lookup"><span data-stu-id="e4c74-118">Instead, rerun setup to replace the missing file.</span></span>  

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="e4c74-119">適用於 VsDevCmd.BAT 的可用選項</span><span class="sxs-lookup"><span data-stu-id="e4c74-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="e4c74-120">若要查看適用於 VsDevCmd.BAT 的可用選項，請搭配 `-help` 選項執行命令：</span><span class="sxs-lookup"><span data-stu-id="e4c74-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>
```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="e4c74-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4c74-121">See Also</span></span>  

- [<span data-ttu-id="e4c74-122">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="e4c74-122">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
