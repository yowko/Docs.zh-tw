---
title: "/verbose |Microsoft 文件"
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
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
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
ms.openlocfilehash: 62285a727217aa897a83a9e746588c80a2c519c0
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="verbose"></a><span data-ttu-id="9228b-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="9228b-102">/verbose</span></span>
<span data-ttu-id="9228b-103">讓編譯器產生詳細的狀態和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="9228b-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9228b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9228b-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9228b-105">引數</span><span class="sxs-lookup"><span data-stu-id="9228b-105">Arguments</span></span>  
 <span data-ttu-id="9228b-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="9228b-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="9228b-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="9228b-107">Optional.</span></span> <span data-ttu-id="9228b-108">指定`/verbose`等同於指定`/verbose+`，這會使編譯器發出詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="9228b-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="9228b-109">此選項的預設值是`/verbose-`。</span><span class="sxs-lookup"><span data-stu-id="9228b-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9228b-110">備註</span><span class="sxs-lookup"><span data-stu-id="9228b-110">Remarks</span></span>  
 <span data-ttu-id="9228b-111">`/verbose`選項顯示編譯器所發出的錯誤總數的相關資訊、 報告哪些組件正在載入的模組，以及顯示目前正在進行編譯的檔案。</span><span class="sxs-lookup"><span data-stu-id="9228b-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9228b-112">`/verbose`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="9228b-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9228b-113">範例</span><span class="sxs-lookup"><span data-stu-id="9228b-113">Example</span></span>  
 <span data-ttu-id="9228b-114">下列程式碼編譯`In.vb`，並指示編譯器顯示詳細的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="9228b-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9228b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9228b-115">See Also</span></span>  
 <span data-ttu-id="9228b-116">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="9228b-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="9228b-117"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="9228b-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
