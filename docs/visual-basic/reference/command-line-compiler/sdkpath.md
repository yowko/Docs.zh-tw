---
title: "/sdkpath |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
dev_langs:
- VB
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
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
ms.openlocfilehash: 2e32bb403347063edcf0d47fd4a7511a0da1f340
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="sdkpath"></a><span data-ttu-id="5d6da-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="5d6da-102">/sdkpath</span></span>
<span data-ttu-id="5d6da-103">指定 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的位置。</span><span class="sxs-lookup"><span data-stu-id="5d6da-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d6da-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d6da-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="5d6da-105">引數</span><span class="sxs-lookup"><span data-stu-id="5d6da-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="5d6da-106">包含要用於編譯的 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本的目錄。</span><span class="sxs-lookup"><span data-stu-id="5d6da-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="5d6da-107">這個路徑不會驗證之前載入。</span><span class="sxs-lookup"><span data-stu-id="5d6da-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="5d6da-108">將目錄名稱括在引號 ("") 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="5d6da-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d6da-109">備註</span><span class="sxs-lookup"><span data-stu-id="5d6da-109">Remarks</span></span>  
 <span data-ttu-id="5d6da-110">此選項會告知[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器從非預設位置載入 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的檔案。</span><span class="sxs-lookup"><span data-stu-id="5d6da-110">This option tells the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="5d6da-111">`/sdkpath`選項設計來搭配[/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)。</span><span class="sxs-lookup"><span data-stu-id="5d6da-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="5d6da-112">[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]使用不同版本的支援程式庫，以避免使用的類型和語言功能的裝置上找不到。</span><span class="sxs-lookup"><span data-stu-id="5d6da-112">The [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d6da-113">`/sdkpath`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="5d6da-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="5d6da-114">`/sdkpath`時設定選項[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]載入裝置專案。</span><span class="sxs-lookup"><span data-stu-id="5d6da-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="5d6da-115">您可以指定編譯器應該使用編譯 Visual Basic 執行階段程式庫的參考不`/vbruntime`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="5d6da-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="5d6da-116">如需詳細資訊，請參閱[/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)。</span><span class="sxs-lookup"><span data-stu-id="5d6da-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d6da-117">範例</span><span class="sxs-lookup"><span data-stu-id="5d6da-117">Example</span></span>  
 <span data-ttu-id="5d6da-118">下列程式碼編譯`Myfile.vb`與[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]，使用 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中的預設安裝目錄中找到[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]C 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="5d6da-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] on the C drive.</span></span> <span data-ttu-id="5d6da-119">一般而言，您可使用的最新版本[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d6da-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d6da-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d6da-120">See Also</span></span>  
 <span data-ttu-id="5d6da-121">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="5d6da-121">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="5d6da-122"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="5d6da-122"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="5d6da-123"> [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) </span><span class="sxs-lookup"><span data-stu-id="5d6da-123"> [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) </span></span>  
<span data-ttu-id="5d6da-124"> [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)</span><span class="sxs-lookup"><span data-stu-id="5d6da-124"> [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)</span></span>
