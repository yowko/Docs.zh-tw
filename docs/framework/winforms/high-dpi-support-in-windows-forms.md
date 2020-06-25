---
title: 高 DPI 支援
description: 如需常見的高 DPI 和動態 DPI 案例，請瞭解 Windows Forms 中的支援。 另請瞭解如何設定 Windows Forms 應用程式，以提供高 DPI 支援。
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a9e0766307095da447c772de5a3065c18b7b7154
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325643"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="576a5-104">Windows Forms 中的高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="576a5-104">High DPI support in Windows Forms</span></span>

<span data-ttu-id="576a5-105">從 .NET Framework 4.7 開始，Windows Forms 包含常見高 DPI 和動態 DPI 案例的增強功能。</span><span class="sxs-lookup"><span data-stu-id="576a5-105">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="576a5-106">其中包括：</span><span class="sxs-lookup"><span data-stu-id="576a5-106">These include:</span></span>

- <span data-ttu-id="576a5-107">改善數個 Windows Forms 控制項（例如控制項和控制項）的縮放和版面配置 <xref:System.Windows.Forms.MonthCalendar> <xref:System.Windows.Forms.CheckedListBox> 。</span><span class="sxs-lookup"><span data-stu-id="576a5-107">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="576a5-108">單一傳遞調整。</span><span class="sxs-lookup"><span data-stu-id="576a5-108">Single-pass scaling.</span></span>  <span data-ttu-id="576a5-109">在 .NET Framework 4.6 和舊版中，縮放是透過多個階段來執行，這會導致某些控制項的縮放比例超出所需。</span><span class="sxs-lookup"><span data-stu-id="576a5-109">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="576a5-110">支援動態 DPI 案例，在這種情況下，使用者會在啟動 Windows Forms 應用程式之後變更 DPI 或縮放比例。</span><span class="sxs-lookup"><span data-stu-id="576a5-110">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="576a5-111">從 .NET Framework 4.7 開始的 .NET Framework 版本中，增強的高 DPI 支援是加入宣告的功能。</span><span class="sxs-lookup"><span data-stu-id="576a5-111">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="576a5-112">您必須設定應用程式來利用它。</span><span class="sxs-lookup"><span data-stu-id="576a5-112">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="576a5-113">設定 Windows Forms 應用程式以提供高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="576a5-113">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="576a5-114">支援高 DPI 感知的新 Windows Forms 功能僅適用于以 .NET Framework 4.7 為目標的應用程式，而且會在 windows 作業系統上執行，從 Windows 10 建立者更新開始。</span><span class="sxs-lookup"><span data-stu-id="576a5-114">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="576a5-115">此外，若要在 Windows Forms 應用程式中設定高 DPI 支援，您必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="576a5-115">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="576a5-116">宣告與 Windows 10 的相容性。</span><span class="sxs-lookup"><span data-stu-id="576a5-116">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="576a5-117">若要這麼做，請將下列內容新增至您的資訊清單檔案：</span><span class="sxs-lookup"><span data-stu-id="576a5-117">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="576a5-118">啟用*app.config*檔案中的個別監視器 DPI 感知。</span><span class="sxs-lookup"><span data-stu-id="576a5-118">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="576a5-119">Windows Forms 引進新的 [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) 元素，以支援從 .NET Framework 4.7 開始新增的新功能和自訂專案。</span><span class="sxs-lookup"><span data-stu-id="576a5-119">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="576a5-120">若要利用支援高 DPI 的新功能，請在您的應用程式佈建檔中新增下列各項。</span><span class="sxs-lookup"><span data-stu-id="576a5-120">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="576a5-121">在舊版的 .NET Framework 中，您使用了資訊清單來新增高 DPI 支援。</span><span class="sxs-lookup"><span data-stu-id="576a5-121">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="576a5-122">不再建議使用此方法，因為它會覆寫在 app.config 檔案上定義的設定。</span><span class="sxs-lookup"><span data-stu-id="576a5-122">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="576a5-123">呼叫靜態 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="576a5-123">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="576a5-124">這應該是應用程式進入點中的第一個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="576a5-124">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="576a5-125">例如：</span><span class="sxs-lookup"><span data-stu-id="576a5-125">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="576a5-126">退出個別的高 DPI 功能</span><span class="sxs-lookup"><span data-stu-id="576a5-126">Opting out of individual high DPI features</span></span>

<span data-ttu-id="576a5-127">將值設定為，會 `DpiAwareness` `PerMonitorV2` 啟用從 .NET Framework 4.7 開始 .NET Framework 版本所支援的所有高 DPI 感知功能。</span><span class="sxs-lookup"><span data-stu-id="576a5-127">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="576a5-128">一般來說，這適用于大部分的 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="576a5-128">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="576a5-129">不過，您可能會想要退出宣告一或多個個別的功能。</span><span class="sxs-lookup"><span data-stu-id="576a5-129">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="576a5-130">執行此作業最重要的原因是您現有的應用程式程式碼已處理該功能。</span><span class="sxs-lookup"><span data-stu-id="576a5-130">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="576a5-131">例如，如果您的應用程式處理自動調整，您可能會想要停用自動調整大小功能，如下所示：</span><span class="sxs-lookup"><span data-stu-id="576a5-131">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="576a5-132">如需個別金鑰和其值的清單，請參閱[Windows Forms 新增設定元素](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)。</span><span class="sxs-lookup"><span data-stu-id="576a5-132">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="576a5-133">新的 DPI 變更事件</span><span class="sxs-lookup"><span data-stu-id="576a5-133">New DPI change events</span></span>

<span data-ttu-id="576a5-134">從 .NET Framework 4.7 開始，三個新的事件可讓您以程式設計方式處理動態 DPI 變更：</span><span class="sxs-lookup"><span data-stu-id="576a5-134">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="576a5-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>，當控制項的 DPI 設定在它的父控制項或表單發生 DPI 變更事件之後，以程式設計方式變更時，就會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="576a5-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="576a5-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>，當控制項的 DPI 設定在其父控制項或表單發生 DPI 變更事件之前，以程式設計方式變更時，就會引發此錯誤。</span><span class="sxs-lookup"><span data-stu-id="576a5-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="576a5-137"><xref:System.Windows.Forms.Form.DpiChanged>，這是在目前顯示表單的顯示裝置上，DPI 設定變更時引發。</span><span class="sxs-lookup"><span data-stu-id="576a5-137"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="576a5-138">新的 helper 方法和屬性</span><span class="sxs-lookup"><span data-stu-id="576a5-138">New helper methods and properties</span></span>

<span data-ttu-id="576a5-139">.NET Framework 4.7 也會新增一些新的 helper 方法和屬性，以提供 DPI 縮放比例的相關資訊，並可讓您執行 DPI 縮放比例。</span><span class="sxs-lookup"><span data-stu-id="576a5-139">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="576a5-140">其中包括：</span><span class="sxs-lookup"><span data-stu-id="576a5-140">These include:</span></span>

- <span data-ttu-id="576a5-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>，可將值從邏輯轉換成裝置圖元。</span><span class="sxs-lookup"><span data-stu-id="576a5-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="576a5-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>，可將點陣圖影像調整為裝置的邏輯 DPI。</span><span class="sxs-lookup"><span data-stu-id="576a5-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="576a5-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>，它會傳回目前裝置的 DPI。</span><span class="sxs-lookup"><span data-stu-id="576a5-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="576a5-144">版本設定考慮</span><span class="sxs-lookup"><span data-stu-id="576a5-144">Versioning considerations</span></span>

<span data-ttu-id="576a5-145">除了在 .NET Framework 4.7 和 Windows 10 建立者更新上執行之外，您的應用程式也可能會在與高 DPI 改良功能不相容的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="576a5-145">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="576a5-146">在此情況下，您必須為您的應用程式開發一個 fallback。</span><span class="sxs-lookup"><span data-stu-id="576a5-146">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="576a5-147">您可以執行此動作，以執行[自訂繪圖](./controls/user-drawn-controls.md)來處理調整。</span><span class="sxs-lookup"><span data-stu-id="576a5-147">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="576a5-148">若要這樣做，您也必須判斷您的應用程式執行所在的作業系統。</span><span class="sxs-lookup"><span data-stu-id="576a5-148">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="576a5-149">您可以使用如下的程式碼來執行此動作：</span><span class="sxs-lookup"><span data-stu-id="576a5-149">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="576a5-150">請注意，如果您的應用程式未在應用程式資訊清單中列為受支援的作業系統，則不會成功偵測到 Windows 10。</span><span class="sxs-lookup"><span data-stu-id="576a5-150">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="576a5-151">您也可以檢查用來建立應用程式的 .NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="576a5-151">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="576a5-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="576a5-152">See also</span></span>

- [<span data-ttu-id="576a5-153">Windows Forms 新增 Configuration 元素</span><span class="sxs-lookup"><span data-stu-id="576a5-153">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="576a5-154">調整 Windows Forms 的大小和比例</span><span class="sxs-lookup"><span data-stu-id="576a5-154">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)
