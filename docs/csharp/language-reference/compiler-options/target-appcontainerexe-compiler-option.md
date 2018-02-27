---
title: "-target:appcontainerexe (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 61fc914b0d956bcca8e0d574296fa0723b0e1406
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2018
---
# <a name="-targetappcontainerexe-c-compiler-options"></a><span data-ttu-id="e4ba9-102">-target:appcontainerexe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="e4ba9-102">-target:appcontainerexe (C# Compiler Options)</span></span>
<span data-ttu-id="e4ba9-103">如果您使用 **-target:appcontainerexe** 編譯器選項，編譯器會建立一個必須在應用程式容器中執行的 Windows 可執行檔 (.exe)。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-103">If you use the **-target:appcontainerexe** compiler option, the compiler creates a Windows executable (.exe) file that must be run in an app container.</span></span> <span data-ttu-id="e4ba9-104">這個選項相當於 [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)，但是專為 [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] 應用程式所設計。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-104">This option is equivalent to [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) but is designed for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ba9-105">語法</span><span class="sxs-lookup"><span data-stu-id="e4ba9-105">Syntax</span></span>  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4ba9-106">備註</span><span class="sxs-lookup"><span data-stu-id="e4ba9-106">Remarks</span></span>  
 <span data-ttu-id="e4ba9-107">這個選項會在 [Portable Executable](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) (可攜式執行檔) (PE) 中設定一個位元，以要求應用程式在應用程式容器中執行。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-107">To require the app to run in an app container, this option sets a bit in the [Portable Executable](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) (PE) file.</span></span> <span data-ttu-id="e4ba9-108">當這個位元設定時，如果 CreateProcess 方法嘗試在應用程式容器之外啟動可執行檔，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-108">When that bit is set, an error occurs if the CreateProcess method tries to launch the executable file outside an app container.</span></span>  
  
 <span data-ttu-id="e4ba9-109">除非您使用 [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔案名稱，否則輸出檔案名稱會採用包含 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法的輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-109">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="e4ba9-110">如果您在命令提示字元指定這個選項，下一個 **-out** 或 **-target** 選項之前的所有檔案都是用來建立可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-110">When you specify this option at a command prompt, all files until the next **-out** or **-target** option are used to create the executable file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a><span data-ttu-id="e4ba9-111">若要在 IDE 中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="e4ba9-111">To set this compiler option in the IDE</span></span>  
  
1.  <span data-ttu-id="e4ba9-112">在方案總管中，開啟專案的捷徑功能表，然後選擇 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-112">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="e4ba9-113">在 [應用程式] 索引標籤上，選擇 [輸出類型] 清單中的 [Windows 市集應用程式]。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-113">On the **Application** tab, in the **Output type** list, choose **Windows Store App**.</span></span>  
  
     <span data-ttu-id="e4ba9-114">這個選項只適用於 [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)]應用程式範本。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-114">This option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="e4ba9-115">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-115">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4ba9-116">範例</span><span class="sxs-lookup"><span data-stu-id="e4ba9-116">Example</span></span>  
 <span data-ttu-id="e4ba9-117">下列命令會將 `filename.cs` 編譯至一個只能在應用程式容器中執行的 Windows 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="e4ba9-117">The following command compiles `filename.cs` into a Windows executable file that can be run only in an app container.</span></span>  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4ba9-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4ba9-118">See Also</span></span>  
 [<span data-ttu-id="e4ba9-119">-target (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="e4ba9-119">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="e4ba9-120">-target:winexe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="e4ba9-120">-target:winexe (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [<span data-ttu-id="e4ba9-121">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="e4ba9-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
