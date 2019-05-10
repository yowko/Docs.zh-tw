---
title: HOW TO：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 93949f003a55cdf67c4ecde988d268728c75e081
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614690"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="94687-102">HOW TO：使用 BindingSource 和 INotifyPropertyChanged 介面引發變更通知</span><span class="sxs-lookup"><span data-stu-id="94687-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="94687-103">當資料來源中包含的類型實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，並且在屬性值變更時引發 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件，<xref:System.Windows.Forms.BindingSource> 元件將會自動偵測資料來源中的變更。</span><span class="sxs-lookup"><span data-stu-id="94687-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="94687-104">這很有用，因為當資料來源值變更時，繫結至 <xref:System.Windows.Forms.BindingSource> 的控制項就會自動更新。</span><span class="sxs-lookup"><span data-stu-id="94687-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94687-105">如果您的資料來源實作 <xref:System.ComponentModel.INotifyPropertyChanged>，而您正在執行非同步作業，您就不應該對背景執行緒上的資料來源進行變更。</span><span class="sxs-lookup"><span data-stu-id="94687-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="94687-106">相反地，您應該讀取背景執行緒上的資料，並將該資料合併至 UI 執行緒上的清單中。</span><span class="sxs-lookup"><span data-stu-id="94687-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94687-107">範例</span><span class="sxs-lookup"><span data-stu-id="94687-107">Example</span></span>  
 <span data-ttu-id="94687-108">下列程式碼範例示範 <xref:System.ComponentModel.INotifyPropertyChanged> 介面的簡單實作。</span><span class="sxs-lookup"><span data-stu-id="94687-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="94687-109">它也會示範當 <xref:System.Windows.Forms.BindingSource> 繫結至 <xref:System.ComponentModel.INotifyPropertyChanged> 類型的清單時，<xref:System.Windows.Forms.BindingSource> 如何自動將資料來源變更傳遞至繫結的控制項。</span><span class="sxs-lookup"><span data-stu-id="94687-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="94687-110">如果您使用 `CallerMemberName` 屬性 (attribute)，呼叫 `NotifyPropertyChanged` 方法時，不需要指定屬性 (property) 名稱做為字串引數。</span><span class="sxs-lookup"><span data-stu-id="94687-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="94687-111">如需詳細資訊，請參閱 <<c0> [ 呼叫端資訊 (C#)](../../../csharp/programming-guide/concepts/caller-information.md)或是[呼叫端資訊 (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md)。</c0></span><span class="sxs-lookup"><span data-stu-id="94687-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94687-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="94687-112">Compiling the Code</span></span>  
 <span data-ttu-id="94687-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="94687-113">This example requires:</span></span>  
  
- <span data-ttu-id="94687-114">System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="94687-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="94687-115">Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="94687-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="94687-116">您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="94687-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span> <span data-ttu-id="94687-117">另請參閱[How to:編譯並執行完整的 Windows Form 程式碼範例使用 Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="94687-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94687-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94687-118">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="94687-119">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="94687-119">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="94687-120">如何：使用 BindingSource ResetItem 方法引發變更通知</span><span class="sxs-lookup"><span data-stu-id="94687-120">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
