---
title: HOW TO：將沒有使用者介面的控制項新增至 Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: bc1f844e5a2cf4d4f3b64ebf20e935f36ff85e12
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987106"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a><span data-ttu-id="fcd21-102">作法：將沒有使用者介面的控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcd21-102">How to: Add Controls Without a User Interface to Windows Forms</span></span>

<span data-ttu-id="fcd21-103">非視覺化的控制項 (或元件) 會為您的應用程式提供功能。</span><span class="sxs-lookup"><span data-stu-id="fcd21-103">A nonvisual control (or component) provides functionality to your application.</span></span> <span data-ttu-id="fcd21-104">不同于其他控制項, 元件不會提供使用者介面給使用者, 因此不需要在 Windows Form 設計工具表面上顯示。</span><span class="sxs-lookup"><span data-stu-id="fcd21-104">Unlike other controls, components do not provide a user interface to the user and thus do not need to be displayed on the Windows Forms Designer surface.</span></span> <span data-ttu-id="fcd21-105">將元件新增至表單時, Windows Form 設計工具會在顯示所有元件的表單底部顯示可調整大小的紙匣。</span><span class="sxs-lookup"><span data-stu-id="fcd21-105">When a component is added to a form, the Windows Forms Designer displays a resizable tray at the bottom of the form where all components are displayed.</span></span> <span data-ttu-id="fcd21-106">一旦控制項加入至元件匣, 您就可以選取元件, 並設定其屬性, 就像您在表單上的任何其他控制項一樣。</span><span class="sxs-lookup"><span data-stu-id="fcd21-106">Once a control has been added to the component tray, you can select the component and set its properties as you would any other control on the form.</span></span>

## <a name="add-a-component-to-a-windows-form"></a><span data-ttu-id="fcd21-107">將元件新增至 Windows Form</span><span class="sxs-lookup"><span data-stu-id="fcd21-107">Add a component to a Windows Form</span></span>

1. <span data-ttu-id="fcd21-108">在 Visual Studio 中開啟表單。</span><span class="sxs-lookup"><span data-stu-id="fcd21-108">Open the form in Visual Studio.</span></span> <span data-ttu-id="fcd21-109">如需詳細資訊，請參閱[如何：在設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))工具中顯示 Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="fcd21-109">For details, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="fcd21-110">在 [**工具箱**] 中, 按一下元件, 並將它拖曳至您的表單。</span><span class="sxs-lookup"><span data-stu-id="fcd21-110">In the **Toolbox**, click a component and drag it to your form.</span></span>

     <span data-ttu-id="fcd21-111">您的元件會出現在元件匣中。</span><span class="sxs-lookup"><span data-stu-id="fcd21-111">Your component appears in the component tray.</span></span>

<span data-ttu-id="fcd21-112">此外, 您可以在執行時間將元件加入至表單。</span><span class="sxs-lookup"><span data-stu-id="fcd21-112">Furthermore, components can be added to a form at run time.</span></span> <span data-ttu-id="fcd21-113">這是常見的案例, 特別是因為元件沒有視覺運算式, 不同于具有使用者介面的控制項。</span><span class="sxs-lookup"><span data-stu-id="fcd21-113">This is a common scenario, especially because components do not have a visual expression, unlike controls that have a user interface.</span></span> <span data-ttu-id="fcd21-114">在下列範例中, <xref:System.Windows.Forms.Timer>會在執行時間新增元件。</span><span class="sxs-lookup"><span data-stu-id="fcd21-114">In the example below, a <xref:System.Windows.Forms.Timer> component is added at run time.</span></span> <span data-ttu-id="fcd21-115">(請注意, Visual Studio 包含許多不同的計時器, 在此情況下, 請使用<xref:System.Windows.Forms.Timer> Windows Forms 元件。</span><span class="sxs-lookup"><span data-stu-id="fcd21-115">(Note that Visual Studio contains a number of different timers; in this case, use a Windows Forms <xref:System.Windows.Forms.Timer> component.</span></span> <span data-ttu-id="fcd21-116">如需 Visual Studio 中不同計時器的詳細資訊, 請參閱[以伺服器為基礎的計時器簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)))。</span><span class="sxs-lookup"><span data-stu-id="fcd21-116">For more information about the different timers in Visual Studio, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).)</span></span>

> [!CAUTION]
> <span data-ttu-id="fcd21-117">元件通常會有控制項特有的屬性, 必須設定此元件才能有效地運作。</span><span class="sxs-lookup"><span data-stu-id="fcd21-117">Components often have control-specific properties that must be set for the component to function effectively.</span></span> <span data-ttu-id="fcd21-118">在下面的<xref:System.Windows.Forms.Timer>元件案例中, 您可以`Interval`設定屬性。</span><span class="sxs-lookup"><span data-stu-id="fcd21-118">In the case of the <xref:System.Windows.Forms.Timer> component below, you set the `Interval` property.</span></span> <span data-ttu-id="fcd21-119">請確定在將元件加入至專案時, 您會設定該元件所需的屬性。</span><span class="sxs-lookup"><span data-stu-id="fcd21-119">Be sure, when adding components to your project, that you set the properties necessary for that component.</span></span>

## <a name="add-a-component-to-a-windows-form-programmatically"></a><span data-ttu-id="fcd21-120">以程式設計方式將元件新增至 Windows Form</span><span class="sxs-lookup"><span data-stu-id="fcd21-120">Add a component to a Windows Form programmatically</span></span>

1. <span data-ttu-id="fcd21-121">在程式碼中建立<xref:System.Windows.Forms.Timer>類別的實例。</span><span class="sxs-lookup"><span data-stu-id="fcd21-121">Create an instance of the <xref:System.Windows.Forms.Timer> class in code.</span></span>

2. <span data-ttu-id="fcd21-122">`Interval`設定屬性, 以決定計時器的刻度之間的時間。</span><span class="sxs-lookup"><span data-stu-id="fcd21-122">Set the `Interval` property to determine the time between ticks of the timer.</span></span>

3. <span data-ttu-id="fcd21-123">為您的元件設定任何其他必要的屬性。</span><span class="sxs-lookup"><span data-stu-id="fcd21-123">Configure any other necessary properties for your component.</span></span>

     <span data-ttu-id="fcd21-124">下列程式碼示範如何<xref:System.Windows.Forms.Timer>建立, 並將其`Interval`屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="fcd21-124">The following code shows the creation of a <xref:System.Windows.Forms.Timer> with its `Interval` property set.</span></span>

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="fcd21-125">藉由參考惡意的 UserControl, 您可能會透過網路來公開本機電腦的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="fcd21-125">You might expose your local computer to a security risk through the network by referencing a malicious UserControl.</span></span> <span data-ttu-id="fcd21-126">這只是在惡意人士建立損毀的自訂控制項, 然後誤將它新增至專案時的問題。</span><span class="sxs-lookup"><span data-stu-id="fcd21-126">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcd21-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcd21-127">See also</span></span>

- [<span data-ttu-id="fcd21-128">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="fcd21-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="fcd21-129">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcd21-129">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="fcd21-130">如何：將 ActiveX 控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcd21-130">How to: Add ActiveX Controls to Windows Forms</span></span>](how-to-add-activex-controls-to-windows-forms.md)
- [<span data-ttu-id="fcd21-131">將控制項加入 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcd21-131">Putting Controls on Windows Forms</span></span>](putting-controls-on-windows-forms.md)
- [<span data-ttu-id="fcd21-132">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="fcd21-132">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="fcd21-133">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="fcd21-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="fcd21-134">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="fcd21-134">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
