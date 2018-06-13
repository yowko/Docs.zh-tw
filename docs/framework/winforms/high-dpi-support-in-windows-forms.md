---
title: 在 Windows Form 中的高 DPI 支援
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbf2d7b61b34a2cd4641a77ee1f2fcdff7f3c3fe
ms.sourcegitcommit: b7763f3435635850a76d4cbcf09bdce6c019208a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/25/2018
ms.locfileid: "34483537"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="c12a2-102">在 Windows Form 中的高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="c12a2-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="c12a2-103">從.NET Framework 4.7 開始，Windows Form 包含常見的高 DPI 與動態 DPI 情節的增強功能。</span><span class="sxs-lookup"><span data-stu-id="c12a2-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="c12a2-104">它們包括：</span><span class="sxs-lookup"><span data-stu-id="c12a2-104">These include:</span></span> 

- <span data-ttu-id="c12a2-105">改良的縮放比例和 Windows Form 的數字的版面配置控制項，例如<xref:System.Windows.Forms.MonthCalendar>控制項和<xref:System.Windows.Forms.CheckedListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="c12a2-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="c12a2-106">單次縮放比例。</span><span class="sxs-lookup"><span data-stu-id="c12a2-106">Single-pass scaling.</span></span>  <span data-ttu-id="c12a2-107">在 .NET Framework 4.6 及更早版本，透過多個行程，這會造成部分控制項，以調整多個必要執行縮放比例。</span><span class="sxs-lookup"><span data-stu-id="c12a2-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="c12a2-108">支援動態 DPI 案例，已啟動的 Windows Form 應用程式之後變更 DPI 或小數位數因素的使用者。</span><span class="sxs-lookup"><span data-stu-id="c12a2-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="c12a2-109">在.NET Framework 4.7 為開頭的.NET framework 版本中，增強高 DPI 支援是選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="c12a2-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="c12a2-110">您必須設定您的應用程式利用.net framework。</span><span class="sxs-lookup"><span data-stu-id="c12a2-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="c12a2-111">設定您的 Windows Form 應用程式的高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="c12a2-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="c12a2-112">支援高 DPI 感知的新 Windows Form 功能是僅適用於目標.NET Framework 4.7 和開頭為 Windows 10 建立者更新的 Windows 作業系統上執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c12a2-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="c12a2-113">此外，若要設定高 DPI 支援在 Windows Form 應用程式中，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c12a2-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="c12a2-114">宣告與 Windows 10 的相容性。</span><span class="sxs-lookup"><span data-stu-id="c12a2-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="c12a2-115">若要這樣做，請加入下列程式資訊清單檔案：</span><span class="sxs-lookup"><span data-stu-id="c12a2-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="c12a2-116">啟用每個監視 DPI 感知*app.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="c12a2-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="c12a2-117">Windows Form 導入了新[ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md)元素來支援新功能和自訂加入開頭為.NET Framework 4.7。</span><span class="sxs-lookup"><span data-stu-id="c12a2-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="c12a2-118">若要充分利用支援高 DPI 的新功能，加上下列應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="c12a2-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="c12a2-119">在舊版的.NET Framework 中，您會使用資訊清單加入高 DPI 支援。</span><span class="sxs-lookup"><span data-stu-id="c12a2-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="c12a2-120">不建議這種方法，因為它會覆寫 app.config 檔案中所定義的設定。</span><span class="sxs-lookup"><span data-stu-id="c12a2-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="c12a2-121">呼叫靜態<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c12a2-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="c12a2-122">這應該是第一個方法呼叫您的應用程式進入點。</span><span class="sxs-lookup"><span data-stu-id="c12a2-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="c12a2-123">例如: </span><span class="sxs-lookup"><span data-stu-id="c12a2-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="c12a2-124">選擇退出個別的高 DPI 功能</span><span class="sxs-lookup"><span data-stu-id="c12a2-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="c12a2-125">設定`DpiAwareness`值設定為`PerMonitorV2`可讓從.NET Framework 4.7 的.NET Framework 版本所支援的所有高 DPI 感知功能。</span><span class="sxs-lookup"><span data-stu-id="c12a2-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="c12a2-126">一般而言，這樣已足夠大多數的 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c12a2-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="c12a2-127">不過，您可以選擇不使用一或多個個別的功能。</span><span class="sxs-lookup"><span data-stu-id="c12a2-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="c12a2-128">執行此作業最重要的原因是現有的應用程式程式碼已經處理該功能。</span><span class="sxs-lookup"><span data-stu-id="c12a2-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="c12a2-129">比方說，如果您的應用程式會處理自動調整，您可能想要停用自動調整大小功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c12a2-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="c12a2-130">如需個別的索引鍵和其值的清單，請參閱[Windows Form 加入組態項目](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)。</span><span class="sxs-lookup"><span data-stu-id="c12a2-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="c12a2-131">新的 DPI 變更事件</span><span class="sxs-lookup"><span data-stu-id="c12a2-131">New DPI change events</span></span>

<span data-ttu-id="c12a2-132">從.NET Framework 4.7 開始，三個新的事件可讓您以程式設計方式處理動態 DPI 變更：</span><span class="sxs-lookup"><span data-stu-id="c12a2-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="c12a2-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>它的父控制項的 DPI 變更事件之後以程式設計方式變更控制項的 DPI 設定或表單發生時引發的。</span><span class="sxs-lookup"><span data-stu-id="c12a2-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="c12a2-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>其父控制項的 DPI 變更事件之前以程式設計方式變更控制項的 DPI 設定或表單發生時引發的。</span><span class="sxs-lookup"><span data-stu-id="c12a2-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="c12a2-135"><xref:System.Windows.Forms.Form.DpiChanged>其中顯示裝置目前顯示表單上的 DPI 設定變更時引發。</span><span class="sxs-lookup"><span data-stu-id="c12a2-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="c12a2-136">新的協助程式方法和屬性</span><span class="sxs-lookup"><span data-stu-id="c12a2-136">New helper methods and properties</span></span>

<span data-ttu-id="c12a2-137">.NET Framework 4.7 也會加入許多新的 helper 方法和屬性，提供 DPI 縮放比例的相關資訊，讓您執行 DPI 縮放比例。</span><span class="sxs-lookup"><span data-stu-id="c12a2-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="c12a2-138">它們包括：</span><span class="sxs-lookup"><span data-stu-id="c12a2-138">These include:</span></span>

- <span data-ttu-id="c12a2-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>可將值從邏輯轉換成裝置像素為單位。</span><span class="sxs-lookup"><span data-stu-id="c12a2-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="c12a2-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>其中縮放邏輯裝置的 DPI 點陣圖影像。</span><span class="sxs-lookup"><span data-stu-id="c12a2-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="c12a2-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>它會傳回目前裝置 DPI。</span><span class="sxs-lookup"><span data-stu-id="c12a2-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="c12a2-142">版本控制的考量</span><span class="sxs-lookup"><span data-stu-id="c12a2-142">Versioning considerations</span></span>

<span data-ttu-id="c12a2-143">除了.NET Framework 4.7 和 Windows 10 建立者的更新版上執行，應用程式也可能以不相容高 DPI 的增強功能的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="c12a2-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="c12a2-144">在此情況下，您必須開發應用程式的後援。</span><span class="sxs-lookup"><span data-stu-id="c12a2-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="c12a2-145">您可以執行[自訂繪圖](./controls/user-drawn-controls.md)處理縮放比例。</span><span class="sxs-lookup"><span data-stu-id="c12a2-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="c12a2-146">若要這樣做，您也需要判斷您的應用程式執行所在的作業系統。</span><span class="sxs-lookup"><span data-stu-id="c12a2-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="c12a2-147">您可以執行，具有類似下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c12a2-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="c12a2-148">請注意，您的應用程式不會成功偵測到 Windows 10 是否未列出為支援的作業系統，應用程式資訊清單中。</span><span class="sxs-lookup"><span data-stu-id="c12a2-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="c12a2-149">您也可以檢查應用程式建置時執行的.NET framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c12a2-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="c12a2-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c12a2-150">See also</span></span>

[<span data-ttu-id="c12a2-151">Windows Form 加入組態項目</span><span class="sxs-lookup"><span data-stu-id="c12a2-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[<span data-ttu-id="c12a2-152">調整 Windows Forms 的大小和比例</span><span class="sxs-lookup"><span data-stu-id="c12a2-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
