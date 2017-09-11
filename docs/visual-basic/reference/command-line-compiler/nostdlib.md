---
title: "/nostdlib (Visual Basic) |Microsoft 文件"
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
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
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
ms.openlocfilehash: 046e2b845324ed1c2f8c15bbb029fe84f7693f6e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="nostdlib-visual-basic"></a><span data-ttu-id="5ec44-102">/nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ec44-102">/nostdlib (Visual Basic)</span></span>
<span data-ttu-id="5ec44-103">讓編譯器不會自動參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="5ec44-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ec44-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ec44-104">Syntax</span></span>  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="5ec44-105">備註</span><span class="sxs-lookup"><span data-stu-id="5ec44-105">Remarks</span></span>  
 <span data-ttu-id="5ec44-106">`/nostdlib`選項移除 System.dll 組件的自動參考，並防止編譯器讀取 Vbc.rsp 檔案。</span><span class="sxs-lookup"><span data-stu-id="5ec44-106">The `/nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="5ec44-107">Vbc.rsp 檔案 — 所在 Vbc.exe 檔案的相同目錄中，參考常用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。</span><span class="sxs-lookup"><span data-stu-id="5ec44-107">The Vbc.rsp file—which is located in the same directory as the Vbc.exe file—references the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ec44-108">永遠會參照 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。</span><span class="sxs-lookup"><span data-stu-id="5ec44-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ec44-109">`/nostdlib`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="5ec44-109">The `/nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ec44-110">範例</span><span class="sxs-lookup"><span data-stu-id="5ec44-110">Example</span></span>  
 <span data-ttu-id="5ec44-111">下列程式碼編譯`T2.vb`而不需要參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="5ec44-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="5ec44-112">您必須設定`_MYTYPE`字串 「 空白 」 移除的條件式編譯常數`My`物件。</span><span class="sxs-lookup"><span data-stu-id="5ec44-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ec44-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ec44-113">See Also</span></span>  
 <span data-ttu-id="5ec44-114">[/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="5ec44-114">[/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="5ec44-115"> [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="5ec44-115"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="5ec44-116"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="5ec44-116"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="5ec44-117"> [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)</span><span class="sxs-lookup"><span data-stu-id="5ec44-117"> [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)</span></span>
