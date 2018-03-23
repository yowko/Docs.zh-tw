---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14361c01d13238db8f820b43889716e2528097f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="4f5c4-102">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f5c4-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="4f5c4-103">可讓編譯器不會自動參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="4f5c4-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f5c4-104">Syntax</span></span>  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="4f5c4-105">備註</span><span class="sxs-lookup"><span data-stu-id="4f5c4-105">Remarks</span></span>  
 <span data-ttu-id="4f5c4-106">`-nostdlib`選項會自動參考之 System.dll 組件，並可防止編譯器讀取 Vbc.rsp 檔案進行。</span><span class="sxs-lookup"><span data-stu-id="4f5c4-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="4f5c4-107">Vbc.rsp 檔案，位於與 Vbc.exe 檔案相同的目錄中，參考常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。</span><span class="sxs-lookup"><span data-stu-id="4f5c4-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f5c4-108">一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="4f5c4-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f5c4-109">`-nostdlib`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="4f5c4-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f5c4-110">範例</span><span class="sxs-lookup"><span data-stu-id="4f5c4-110">Example</span></span>  
 <span data-ttu-id="4f5c4-111">下列程式碼編譯`T2.vb`不需參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="4f5c4-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="4f5c4-112">您必須設定`_MYTYPE`字串 「 空白 」 移除的條件式編譯常數`My`物件。</span><span class="sxs-lookup"><span data-stu-id="4f5c4-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f5c4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f5c4-113">See Also</span></span>  
 [<span data-ttu-id="4f5c4-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="4f5c4-114">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="4f5c4-115">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="4f5c4-115">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4f5c4-116">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="4f5c4-116">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="4f5c4-117">自訂 My 中可用的物件</span><span class="sxs-lookup"><span data-stu-id="4f5c4-117">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
