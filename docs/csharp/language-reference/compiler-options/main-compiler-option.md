---
title: "-main (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /main
dev_langs:
- CSharp
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: 7736f257c80f9ad50a47699e404d6dd04fbce808
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="main-c-compiler-options"></a><span data-ttu-id="221a3-102">/main (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="221a3-102">/main (C# Compiler Options)</span></span>
<span data-ttu-id="221a3-103">如果有多個類別包含 **Main** 方法，這個選項會指定含有程式進入點的類別。</span><span class="sxs-lookup"><span data-stu-id="221a3-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="221a3-104">Syntax</span></span>  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="221a3-105">引數</span><span class="sxs-lookup"><span data-stu-id="221a3-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="221a3-106">含有 **Main** 方法的類型。</span><span class="sxs-lookup"><span data-stu-id="221a3-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="221a3-107">備註</span><span class="sxs-lookup"><span data-stu-id="221a3-107">Remarks</span></span>  
 <span data-ttu-id="221a3-108">如果編譯的 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法中包含一個以上的型別，您可以指定哪個型別含有要作為程式進入點的 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="221a3-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="221a3-109">在編譯 .exe 檔案時，即可使用此選項。</span><span class="sxs-lookup"><span data-stu-id="221a3-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="221a3-110">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="221a3-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="221a3-111">開啟專案的 [屬性]**** 頁面。</span><span class="sxs-lookup"><span data-stu-id="221a3-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="221a3-112">按一下 [應用程式]**** 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="221a3-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="221a3-113">修改 [啟始物件]**** 屬性。</span><span class="sxs-lookup"><span data-stu-id="221a3-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="221a3-114">若要以程式設計方式設定此編譯器選項，請參閱 <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>。</span><span class="sxs-lookup"><span data-stu-id="221a3-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="221a3-115">範例</span><span class="sxs-lookup"><span data-stu-id="221a3-115">Example</span></span>  
 <span data-ttu-id="221a3-116">編譯 `t2.cs` 和 `t3.cs`，將 **Main** 方法的位置指定在 `Test2` 中：</span><span class="sxs-lookup"><span data-stu-id="221a3-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="221a3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="221a3-117">See Also</span></span>  
 <span data-ttu-id="221a3-118">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="221a3-118">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="221a3-119"> [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span><span class="sxs-lookup"><span data-stu-id="221a3-119"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span></span>
