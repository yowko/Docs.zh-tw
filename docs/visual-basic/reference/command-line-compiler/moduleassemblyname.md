---
title: "/moduleassemblyname |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: 16
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
ms.openlocfilehash: 6852b8a0d9874fd65e93cdd9507fe9b7119ce5b3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="moduleassemblyname"></a><span data-ttu-id="f4b1a-102">/moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="f4b1a-102">/moduleassemblyname</span></span>
<span data-ttu-id="f4b1a-103">指定將包含此模組的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4b1a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4b1a-104">Syntax</span></span>  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="f4b1a-105">引數</span><span class="sxs-lookup"><span data-stu-id="f4b1a-105">Arguments</span></span>  
  
|<span data-ttu-id="f4b1a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f4b1a-106">Term</span></span>|<span data-ttu-id="f4b1a-107">定義</span><span class="sxs-lookup"><span data-stu-id="f4b1a-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="f4b1a-108">此模組一部分的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4b1a-109">備註</span><span class="sxs-lookup"><span data-stu-id="f4b1a-109">Remarks</span></span>  
 <span data-ttu-id="f4b1a-110">編譯器處理序`/moduleassemblyname`選項才`/target:module`已指定選項。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-110">The compiler processes the `/moduleassemblyname` option only if the `/target:module` option has been specified.</span></span> <span data-ttu-id="f4b1a-111">這會導致編譯器建立模組。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="f4b1a-112">編譯器所建立的模組是僅適用於具有指定的組件`/moduleassemblyname`選項。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-112">The module created by the compiler is valid only for the assembly specified with the `/moduleassemblyname` option.</span></span> <span data-ttu-id="f4b1a-113">如果您將模組放在不同的組件時，會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="f4b1a-114">`/moduleassemblyname`選項只有在下列條件成立時，才需要︰</span><span class="sxs-lookup"><span data-stu-id="f4b1a-114">The `/moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="f4b1a-115">在模組中的資料類型必須能夠存取`Friend`參考的組件的類型。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="f4b1a-116">參考的組件有模組將在其中建置的組件授與 friend 組件存取權限。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="f4b1a-117">如需建立模組的詳細資訊，請參閱[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="f4b1a-118">如需 friend 組件的詳細資訊，請參閱[Friend 組件](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4b1a-119">`/moduleassemblyname`選項不是從 Visual Studio 開發環境中使用; 其只當您編譯的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f4b1a-119">The `/moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b1a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4b1a-120">See Also</span></span>  
 <span data-ttu-id="f4b1a-121">[如何︰ 建置多檔案組件](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-121">[How to: Build a Multifile Assembly](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span></span>  
<span data-ttu-id="f4b1a-122"> [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-122"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="f4b1a-123"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-123"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="f4b1a-124"> [/main](../../../visual-basic/reference/command-line-compiler/main.md) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-124"> [/main](../../../visual-basic/reference/command-line-compiler/main.md) </span></span>  
<span data-ttu-id="f4b1a-125"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-125"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="f4b1a-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span></span>  
<span data-ttu-id="f4b1a-127"> [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-127"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="f4b1a-128"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="f4b1a-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="f4b1a-129"> [Friend 組件](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span><span class="sxs-lookup"><span data-stu-id="f4b1a-129"> [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span></span>
