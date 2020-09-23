---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4fcc5305985f5ba32b3e6ffb740c0611821215d3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097653"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="0d686-102">-nostdlib (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="0d686-102">-nostdlib (Visual Basic)</span></span>

<span data-ttu-id="0d686-103">導致編譯器不自動參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="0d686-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d686-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d686-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="0d686-105">備註</span><span class="sxs-lookup"><span data-stu-id="0d686-105">Remarks</span></span>  

 <span data-ttu-id="0d686-106">`-nostdlib`選項會移除 System.dll 元件的自動參考，並防止編譯器讀取 Vbc 檔。</span><span class="sxs-lookup"><span data-stu-id="0d686-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="0d686-107">Vbc 檔案（位於與 Vbc.exe 檔案相同的目錄中）會參考常用 .NET Framework 元件，並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="0d686-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d686-108">一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 元件。</span><span class="sxs-lookup"><span data-stu-id="0d686-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d686-109">`-nostdlib`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0d686-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d686-110">範例</span><span class="sxs-lookup"><span data-stu-id="0d686-110">Example</span></span>  

 <span data-ttu-id="0d686-111">下列程式碼會進行編譯， `T2.vb` 而不會參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="0d686-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="0d686-112">您必須將 `_MYTYPE` 條件式編譯常數設定為字串 "Empty"，以移除 `My` 物件。</span><span class="sxs-lookup"><span data-stu-id="0d686-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d686-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d686-113">See also</span></span>

- [<span data-ttu-id="0d686-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="0d686-114">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="0d686-115">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0d686-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0d686-116">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="0d686-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="0d686-117">自訂 My 可以使用的物件</span><span class="sxs-lookup"><span data-stu-id="0d686-117">Customizing Which Objects are Available in My</span></span>](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
