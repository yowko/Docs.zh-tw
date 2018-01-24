---
title: "-main (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5f1d06bf408f13a78df503ab10fe3c57b4ff68a3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="eb9e1-102">-main (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="eb9e1-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="eb9e1-103">如果有多個類別包含 **Main** 方法，這個選項會指定含有程式進入點的類別。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb9e1-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb9e1-105">引數</span><span class="sxs-lookup"><span data-stu-id="eb9e1-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="eb9e1-106">含有 **Main** 方法的類型。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb9e1-107">備註</span><span class="sxs-lookup"><span data-stu-id="eb9e1-107">Remarks</span></span>  
 <span data-ttu-id="eb9e1-108">如果編譯的 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法中包含一個以上的型別，您可以指定哪個型別含有要作為程式進入點的 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="eb9e1-109">在編譯 .exe 檔案時，即可使用此選項。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="eb9e1-110">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="eb9e1-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="eb9e1-111">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="eb9e1-112">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="eb9e1-113">修改 [啟始物件] 屬性。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="eb9e1-114">若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。</span><span class="sxs-lookup"><span data-stu-id="eb9e1-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb9e1-115">範例</span><span class="sxs-lookup"><span data-stu-id="eb9e1-115">Example</span></span>  
 <span data-ttu-id="eb9e1-116">編譯 `t2.cs` 和 `t3.cs`，將 **Main** 方法的位置指定在 `Test2` 中：</span><span class="sxs-lookup"><span data-stu-id="eb9e1-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb9e1-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="eb9e1-117">See Also</span></span>  
 [<span data-ttu-id="eb9e1-118">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="eb9e1-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="eb9e1-119">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="eb9e1-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
