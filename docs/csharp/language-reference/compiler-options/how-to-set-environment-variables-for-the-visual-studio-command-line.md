---
title: "如何：為 Visual Studio 命令列設定環境變數"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
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
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8012e310bb04ec3acef0790f9cd50ed42dd9286a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="7f7e9-102">如何：為 Visual Studio 命令列設定環境變數</span><span class="sxs-lookup"><span data-stu-id="7f7e9-102">How to: Set Environment Variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="7f7e9-103">VsDevCmd.bat 檔案設定適當的環境變數來啟用命令列組建。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span> <span data-ttu-id="7f7e9-104">如需 VsDevCmd.bat 的詳細資訊，請參閱[知識庫文件 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042)。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-104">For more information about VsDevCmd.bat, see [Knowledge Base article Q248802](http://go.microsoft.com/fwlink/?LinkId=225042).</span></span>  

> [!NOTE]
> <span data-ttu-id="7f7e9-105">VsDevCmd.bat 檔案是使用 Visual Studio 2017 傳遞新的檔案。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-105">The VsDevCmd.bat file is a new file delivered with Visual Studio 2017.</span></span> <span data-ttu-id="7f7e9-106">Visual Studio 2015 和較早版本用於相同目的 VSVARS32.bat。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-106">Visual Studio 2015 and earlier versions used VSVARS32.bat for the same purpose.</span></span> <span data-ttu-id="7f7e9-107">此檔案儲存在 Visual Studio \Program Files\Microsoft\\*版本*\Common7\Tools 或 Program Files (x86) \Microsoft Visual Studio\\*版本*\Common7\Tools。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-107">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>
  
<span data-ttu-id="7f7e9-108">如果目前版本的 Visual Studio 也有舊版的 Visual Studio 的電腦上安裝，您不應該執行 VsDevCmd.bat 和 vsvars32 以。BAT 從相同的命令提示字元視窗中的不同版本。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-108">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="7f7e9-109">相反地，您應該在它自己的視窗中執行每個版本的命令。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-109">Instead, you should run the command for each version in its own window.</span></span>
  
### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="7f7e9-110">若要執行 VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="7f7e9-110">To run VsDevCmd.BAT</span></span>  
  
1.  <span data-ttu-id="7f7e9-111">從**啟動**功能表中，開啟**VS 2017 的開發人員命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-111">From the **Start** menu, open the **Developer Command Prompt for VS 2017**.</span></span>  <span data-ttu-id="7f7e9-112">處於**Visual Studio 2017**資料夾。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-112">It's in the **Visual Studio 2017** folder.</span></span>
  
2.  <span data-ttu-id="7f7e9-113">將變更為 \Program Files\Microsoft Visual Studio\\*版本*\\*供應項目*\Common7\Tools 或 \Program 檔案 (x86) \Microsoft Visual Studio\\*版本*\\*供應項目*安裝 \Common7\Tools 子目錄。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-113">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="7f7e9-114">(*版本*是*2017年*目前版本。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-114">(*Version* is *2017* for the current version.</span></span> <span data-ttu-id="7f7e9-115">*供應項目*是其中一個*企業*， *Professional*或*社群*。)</span><span class="sxs-lookup"><span data-stu-id="7f7e9-115">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>
  
3.  <span data-ttu-id="7f7e9-116">輸入執行 VsDevCmd.bat **VsDevCmd**。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-116">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="7f7e9-117">VsDevCmd.bat 可以從電腦而異。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-117">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="7f7e9-118">請勿使用 VsDevCmd.bat 從另一部電腦取代 VsDevCmd.bat 檔案遺失或損毀。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-118">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="7f7e9-119">請重新執行安裝程式以取代遺失的檔案。</span><span class="sxs-lookup"><span data-stu-id="7f7e9-119">Instead, rerun setup to replace the missing file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7e9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f7e9-120">See Also</span></span>  
 [<span data-ttu-id="7f7e9-121">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="7f7e9-121">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
