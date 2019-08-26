---
title: -pdb (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602573"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="bc894-102">-pdb (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="bc894-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="bc894-103">**-pdb** 編譯器選項指定偵錯符號檔的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="bc894-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc894-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc894-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc894-105">引數</span><span class="sxs-lookup"><span data-stu-id="bc894-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="bc894-106">偵錯符號檔案的名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="bc894-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc894-107">備註</span><span class="sxs-lookup"><span data-stu-id="bc894-107">Remarks</span></span>  
 <span data-ttu-id="bc894-108">當您指定 [-debug (C# 編譯器選項)](./debug-compiler-option.md) 時，編譯器會在相同的目錄中建立 .pdb 檔案，而編譯器會在此目錄中建立檔案名稱與輸出檔案名稱相同的輸出檔案 (.exe 或 .dll)。</span><span class="sxs-lookup"><span data-stu-id="bc894-108">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="bc894-109">**-pdb** 可讓您指定 .pdb 檔案的非預設檔案名稱和位置。</span><span class="sxs-lookup"><span data-stu-id="bc894-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="bc894-110">無法在 Visual Studio 開發環境中設定此編譯器選項，也無法以程式設計方式進行變更。</span><span class="sxs-lookup"><span data-stu-id="bc894-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc894-111">範例</span><span class="sxs-lookup"><span data-stu-id="bc894-111">Example</span></span>  
 <span data-ttu-id="bc894-112">編譯 `t.cs` 並建立稱為 tt.pdb 的 .pdb 檔案：</span><span class="sxs-lookup"><span data-stu-id="bc894-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc894-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc894-113">See also</span></span>

- [<span data-ttu-id="bc894-114">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="bc894-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="bc894-115">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="bc894-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
