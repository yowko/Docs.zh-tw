---
title: 指定進入點
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 787406b1fa7e5beb59ff3f8715c1215a734ed895
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411300"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="d5a3a-102">指定進入點</span><span class="sxs-lookup"><span data-stu-id="d5a3a-102">Specifying an Entry Point</span></span>
<span data-ttu-id="d5a3a-103">進入點可識別函式在 DLL 中的位置。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-103">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="d5a3a-104">在 Managed 專案中，目標函式的原始名稱或序數進入點可跨越交互操作界限識別該函式。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-104">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="d5a3a-105">此外，您可以將進入點對應到不同的名稱，有效地重新命名函式。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-105">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="d5a3a-106">以下是重新命名 DLL 函式的可能原因清單：</span><span class="sxs-lookup"><span data-stu-id="d5a3a-106">Following is a list of possible reasons to rename a DLL function:</span></span>  
  
-   <span data-ttu-id="d5a3a-107">避免使用區分大小寫的 API 函式名稱</span><span class="sxs-lookup"><span data-stu-id="d5a3a-107">To avoid using case-sensitive API function names</span></span>  
  
-   <span data-ttu-id="d5a3a-108">符合現有的命名標準</span><span class="sxs-lookup"><span data-stu-id="d5a3a-108">To comply with existing naming standards</span></span>  
  
-   <span data-ttu-id="d5a3a-109">容納接受不同資料類型 (藉由宣告相同 DLL 函式的多個版本) 的函式</span><span class="sxs-lookup"><span data-stu-id="d5a3a-109">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
-   <span data-ttu-id="d5a3a-110">簡化使用包含 ANSI 和 Unicode 版本的 API</span><span class="sxs-lookup"><span data-stu-id="d5a3a-110">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="d5a3a-111">本主題示範如何在 Managed 程式碼中重新命名 DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-111">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="d5a3a-112">在 Visual Basic 中重新命名函式</span><span class="sxs-lookup"><span data-stu-id="d5a3a-112">Renaming a Function in Visual Basic</span></span>  
 <span data-ttu-id="d5a3a-113">Visual Basic 使用 **Function** 關鍵字在 **Declare** 陳述式中設定 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 欄位。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-113">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="d5a3a-114">下列範例示範基本宣告。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-114">The following example shows a basic declaration.</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="d5a3a-115">您可以將 **MessageBox** 進入點取代為 **MsgBox**，方法是在您的定義中包含 **Alias** 關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-115">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="d5a3a-116">在這兩個範例中，**Auto** 關鍵字讓您不需要指定進入點的字元集版本。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-116">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="d5a3a-117">如需選取字元集的詳細資訊，請參閱[指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-117">For more information about selecting a character set, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="d5a3a-118">在 C# 和 C++ 中重新命名函式</span><span class="sxs-lookup"><span data-stu-id="d5a3a-118">Renaming a Function in C# and C++</span></span>  
 <span data-ttu-id="d5a3a-119">您可以使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 欄位來依名稱或序數指定 DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-119">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="d5a3a-120">如果方法定義中的函式名稱與 DLL 中的進入點相同，則不必明確地以 **EntryPoint** 欄位來識別函式。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-120">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="d5a3a-121">否則，請使用其中一種下列屬性形式來表示名稱或序數：</span><span class="sxs-lookup"><span data-stu-id="d5a3a-121">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="d5a3a-122">請注意，您必須在序數前面加上井字號 (#)。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-122">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="d5a3a-123">下列範例示範如何使用 **EntryPoint** 欄位，將程式碼中的 **MessageBoxA** 取代為 **MsgBox**。</span><span class="sxs-lookup"><span data-stu-id="d5a3a-123">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class WindowsAPI
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="d5a3a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5a3a-124">See also</span></span>
- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="d5a3a-125">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="d5a3a-125">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="d5a3a-126">平台叫用範例</span><span class="sxs-lookup"><span data-stu-id="d5a3a-126">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="d5a3a-127">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="d5a3a-127">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
