---
title: 自訂控制項中的方法實作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 38dcad25af31b87afc1cc6ef4f89a1f7903bc0ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012759"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="be9b4-102">自訂控制項中的方法實作</span><span class="sxs-lookup"><span data-stu-id="be9b4-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="be9b4-103">在控制項中實作方法的方式，與在其他任何元件中實作方法的方式相同。</span><span class="sxs-lookup"><span data-stu-id="be9b4-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="be9b4-104">在 Visual Basic 中，若方法必須傳回值，會實作為 `Public Function`。</span><span class="sxs-lookup"><span data-stu-id="be9b4-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="be9b4-105">若無須傳回值，便會實作為 `Public Sub`。</span><span class="sxs-lookup"><span data-stu-id="be9b4-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="be9b4-106">方法會透過下列語法宣告：</span><span class="sxs-lookup"><span data-stu-id="be9b4-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="be9b4-107">由於函式需要傳回值，因此必須指定傳回類型，例如 integer、string、object 等等。</span><span class="sxs-lookup"><span data-stu-id="be9b4-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="be9b4-108">程序如有接受引數 `Function` 或 `Sub`，也必須加以指定。</span><span class="sxs-lookup"><span data-stu-id="be9b4-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="be9b4-109">C# 的函式與程序與 Visual Basic 並無差別。</span><span class="sxs-lookup"><span data-stu-id="be9b4-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="be9b4-110">方法會傳回值或傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="be9b4-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="be9b4-111">以下是宣告 C# 公用方法的語法：</span><span class="sxs-lookup"><span data-stu-id="be9b4-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="be9b4-112">當您宣告方法時，應盡可能地將其所有引數宣告成明確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="be9b4-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="be9b4-113">接受物件參考的引數應宣告為特定類型，例如應宣告為 `As Widget`，而不是 `As Object`。</span><span class="sxs-lookup"><span data-stu-id="be9b4-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="be9b4-114">在 Visual Basic 中，預設設定 `Option Strict` 會自動施行此規則。</span><span class="sxs-lookup"><span data-stu-id="be9b4-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="be9b4-115">宣告引數的類型有助於編譯器預先檢出許多開發人員的錯誤，而不是在執行時發生。</span><span class="sxs-lookup"><span data-stu-id="be9b4-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="be9b4-116">編譯器一律會檢查錯誤，而執行時期測試僅具備測試套件的功能。</span><span class="sxs-lookup"><span data-stu-id="be9b4-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="be9b4-117">多載的方法</span><span class="sxs-lookup"><span data-stu-id="be9b4-117">Overloaded Methods</span></span>  
 <span data-ttu-id="be9b4-118">若要允許控制項的使用者提供不同的參數組合給方法，請使用明確的資料類型，為方法提供多個多載。</span><span class="sxs-lookup"><span data-stu-id="be9b4-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="be9b4-119">請避免建立宣告有可能會包含任何資料類型之 `As Object` 的參數，因為這可能會導致測試時無法檢出的錯誤。</span><span class="sxs-lookup"><span data-stu-id="be9b4-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be9b4-120">常見於語言執行時期的通用資料為 `Object`，而不是 `Variant`。</span><span class="sxs-lookup"><span data-stu-id="be9b4-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="be9b4-121">`Variant` 已從語言中移除。</span><span class="sxs-lookup"><span data-stu-id="be9b4-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="be9b4-122">例如假設 `Spin` 控制項的 `Widget` 方法可能會允許直接指定微調的方向及速度，或指定其他角動量要被吸收的 `Widget` 物件：</span><span class="sxs-lookup"><span data-stu-id="be9b4-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="be9b4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be9b4-123">See also</span></span>

- [<span data-ttu-id="be9b4-124">事件</span><span class="sxs-lookup"><span data-stu-id="be9b4-124">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="be9b4-125">Windows Forms 控制項中的屬性</span><span class="sxs-lookup"><span data-stu-id="be9b4-125">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
