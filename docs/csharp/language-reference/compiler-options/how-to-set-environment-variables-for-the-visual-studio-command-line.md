---
title: 如何為 Visual Studio 命令列設定環境變數
ms.date: 12/20/2019
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
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342357"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="ec1fe-102">如何為 Visual Studio 命令列設定環境變數</span><span class="sxs-lookup"><span data-stu-id="ec1fe-102">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="ec1fe-103">VsDevCmd.bat 檔案可設定適當的環境變數，以啟用命令列組建。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-103">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="ec1fe-104">Visual Studio 2015 和舊版使用 VSVARS32.BAT，而非 Vsdevcmd.bat，用於相同的用途。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-104">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="ec1fe-105">此檔案的儲存位置為 \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-105">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="ec1fe-106">如果安裝最新版 Visual Studio 的電腦上也有安裝舊版 Visual Studio，請勿於相同的命令提示字元視窗中，執行不同版本的 VsDevCmd.bat 及 VSVARS32.BAT。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-106">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="ec1fe-107">而是應改為在各版本本身的視窗中執行命令。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-107">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="ec1fe-108">執行 VsDevCmd.BAT</span><span class="sxs-lookup"><span data-stu-id="ec1fe-108">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="ec1fe-109">在 [**開始**] 功能表中，開啟**VS 2019**的 [開發人員命令提示字元]。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-109">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="ec1fe-110">它位於**Visual Studio 2019**資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-110">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="ec1fe-111">根據您的安裝變更到 \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools 或是 \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools 子目錄。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-111">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="ec1fe-112">（目前版本的*版本*是*2019* 。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-112">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="ec1fe-113">*供應項目*為 *Enterprise*、*Professional* 或 *Community* 中的其中一個。)</span><span class="sxs-lookup"><span data-stu-id="ec1fe-113">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="ec1fe-114">鍵入 **VsDevCmd**以執行 VsDevCmd.bat。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-114">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="ec1fe-115">在不同的電腦上，VsDevCmd.bat 檔案可能也不同。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-115">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="ec1fe-116">請勿使用另一部電腦的 VsDevCmd.bat 來取代遺失或損毀的 VsDevCmd.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-116">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="ec1fe-117">請重新執行安裝程式以取代遺失的檔案。</span><span class="sxs-lookup"><span data-stu-id="ec1fe-117">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="ec1fe-118">適用於 VsDevCmd.BAT 的可用選項</span><span class="sxs-lookup"><span data-stu-id="ec1fe-118">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="ec1fe-119">若要查看適用於 VsDevCmd.BAT 的可用選項，請搭配 `-help` 選項執行命令：</span><span class="sxs-lookup"><span data-stu-id="ec1fe-119">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="ec1fe-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec1fe-120">See also</span></span>

- [<span data-ttu-id="ec1fe-121">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="ec1fe-121">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
