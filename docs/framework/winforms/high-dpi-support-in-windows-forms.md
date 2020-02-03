---
title: 高 DPI 支援
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a5c3125475c2de2cf83a3d97e356b26c0acdde99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741893"
---
# <a name="high-dpi-support-in-windows-forms"></a>Windows Forms 中的高 DPI 支援

從 .NET Framework 4.7 開始，Windows Forms 包含常見高 DPI 和動態 DPI 案例的增強功能。 其中包括：

- 改善數個 Windows Forms 控制項的縮放和版面配置，例如 <xref:System.Windows.Forms.MonthCalendar> 控制項和 <xref:System.Windows.Forms.CheckedListBox> 控制項。

- 單一傳遞調整。  在 .NET Framework 4.6 和舊版中，縮放是透過多個階段來執行，這會導致某些控制項的縮放比例超出所需。

- 支援動態 DPI 案例，在這種情況下，使用者會在啟動 Windows Forms 應用程式之後變更 DPI 或縮放比例。

從 .NET Framework 4.7 開始的 .NET Framework 版本中，增強的高 DPI 支援是加入宣告的功能。 您必須設定應用程式來利用它。

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>設定 Windows Forms 應用程式以提供高 DPI 支援

支援高 DPI 感知的新 Windows Forms 功能僅適用于以 .NET Framework 4.7 為目標的應用程式，而且會在 windows 作業系統上執行，從 Windows 10 建立者更新開始。

此外，若要在 Windows Forms 應用程式中設定高 DPI 支援，您必須執行下列動作：

- 宣告與 Windows 10 的相容性。

  若要這麼做，請將下列內容新增至您的資訊清單檔案：

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- 在*app.config*檔案中啟用每個監視器的 DPI 感知。

  Windows Forms 引進新的[`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md)元素，以支援從 .NET Framework 4.7 開始新增的新功能和自訂專案。 若要利用支援高 DPI 的新功能，請在您的應用程式佈建檔中新增下列各項。

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > 在舊版的 .NET Framework 中，您使用了資訊清單來新增高 DPI 支援。 不再建議使用此方法，因為它會覆寫 app.config 檔案中定義的設定。

- 呼叫靜態 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法。

  這應該是應用程式進入點中的第一個方法呼叫。 例如，

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>退出個別的高 DPI 功能

將 `DpiAwareness` 值設定為 `PerMonitorV2`，會啟用從 .NET Framework 4.7 開始 .NET Framework 版本所支援的所有高 DPI 感知功能。 一般來說，這適用于大部分的 Windows Forms 應用程式。 不過，您可能會想要退出宣告一或多個個別的功能。 執行此作業最重要的原因是您現有的應用程式程式碼已處理該功能。  例如，如果您的應用程式處理自動調整，您可能會想要停用自動調整大小功能，如下所示：

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

如需個別金鑰和其值的清單，請參閱[Windows Forms 新增設定元素](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)。

## <a name="new-dpi-change-events"></a>新的 DPI 變更事件

從 .NET Framework 4.7 開始，三個新的事件可讓您以程式設計方式處理動態 DPI 變更：

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>，當控制項的 DPI 設定在其父控制項或表單發生 DPI 變更事件之後，以程式設計方式變更時，就會引發此錯誤。
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>，當控制項的 DPI 設定在其父控制項或表單發生 DPI 變更事件之前，以程式設計方式變更時，就會引發此錯誤。
- <xref:System.Windows.Forms.Form.DpiChanged>，當目前顯示表單的顯示裝置上的 DPI 設定變更時，就會引發此情況。

## <a name="new-helper-methods-and-properties"></a>新的 helper 方法和屬性

.NET Framework 4.7 也會新增一些新的 helper 方法和屬性，以提供 DPI 縮放比例的相關資訊，並可讓您執行 DPI 縮放比例。 其中包括：

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>，會將值從邏輯轉換為裝置圖元。

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>，可將點陣圖影像調整為裝置的邏輯 DPI。

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>，它會傳回目前裝置的 DPI。

## <a name="versioning-considerations"></a>版本設定考慮

除了在 .NET Framework 4.7 和 Windows 10 建立者更新上執行之外，您的應用程式也可能會在與高 DPI 改良功能不相容的環境中執行。 在此情況下，您必須為您的應用程式開發一個 fallback。 您可以執行此動作，以執行[自訂繪圖](./controls/user-drawn-controls.md)來處理調整。

若要這樣做，您也必須判斷您的應用程式執行所在的作業系統。 您可以使用如下的程式碼來執行此動作：

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

請注意，如果您的應用程式未在應用程式資訊清單中列為受支援的作業系統，則不會成功偵測到 Windows 10。

您也可以檢查用來建立應用程式的 .NET Framework 版本：

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>另請參閱

- [Windows Forms 新增 Configuration 元素](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [調整 Windows Forms 的大小和比例](adjusting-the-size-and-scale-of-windows-forms.md)
