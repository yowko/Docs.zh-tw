---
title: Windows Forms 中的高 DPI 支援
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dbb5af9c5cf1d8796544592602c645584d21a04
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711783"
---
# <a name="high-dpi-support-in-windows-forms"></a>Windows Forms 中的高 DPI 支援

從.NET Framework 4.7 開始，Windows Form 包含常見的高 DPI 與動態 DPI 情節的增強功能。 它們包括： 

- 改進調整和配置數個 Windows Form 控制項，例如<xref:System.Windows.Forms.MonthCalendar>控制項和<xref:System.Windows.Forms.CheckedListBox>控制項。 

- 單一行程調整。  在.NET Framework 4.6 和更早版本中，透過多個行程，這造成一些控制項進行調整，多個必須執行調整。

- 已啟動的 Windows Forms 應用程式之後變更的 DPI 或小數位數的比例的使用者的動態 DPI 案例的支援。

從.NET Framework 4.7 開始的.NET framework 版本，增強高 DPI 支援是選擇性功能。 您必須設定您的應用程式加以利用。

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>設定您的 Windows Forms 應用程式的高 DPI 支援

支援高 DPI 感知的新 Windows Forms 功能是僅適用於.NET Framework 4.7 為目標，並從 Windows 10 Creators Update 開始的 Windows 作業系統上執行的應用程式。 

此外，若要設定您的 Windows Forms 應用程式中的高 DPI 支援，您必須執行下列作業：

- 宣告與 Windows 10 的相容性。

  若要這樣做，請將下列內容新增至您的資訊清單檔案：

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- 啟用個別監視器 DPI 感知*app.config*檔案。

  引進新的 Windows Forms [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../configure-apps/file-schema/winforms/index.md)以支援新功能和自訂項目加入從.NET Framework 4.7 開始的項目。 若要充分利用支援高 DPI 的新功能，將下列內容新增至您的應用程式組態檔。   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > 在舊版的.NET Framework 中，您會使用資訊清單新增高 DPI 支援。 不建議這種方法，因為它會覆寫 app.config 檔案中所定義的設定。
   
- 呼叫靜態<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法。
   
  這應該是第一個方法呼叫中的應用程式的進入點。 例如: 
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>退出個別的高 DPI 功能

設定`DpiAwareness`值`PerMonitorV2`可讓從.NET Framework 4.7 開始的.NET Framework 版本所支援的所有高 DPI 感知功能。 一般而言，這是適合大部分的 Windows Forms 應用程式。 不過，您可以選擇不使用一或多個個別的功能。 執行此動作的最重要的原因是您現有的應用程式程式碼已經處理該功能。  比方說，如果您的應用程式會處理自動調整規模，您可能想要停用自動調整大小功能，如下所示：

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

如需個別的索引鍵和其值的清單，請參閱 < [Windows Form 加入組態項目](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)。

## <a name="new-dpi-change-events"></a>新的 DPI 變更事件

從.NET Framework 4.7 開始，三個新的事件可讓您以程式設計方式處理動態 DPI 變更：

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>這會引發之後的父控制項的 DPI 變更事件以程式設計方式變更控制項的 DPI 設定或表單發生時。
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>這會引發其父控制項的 DPI 變更事件之前以程式設計方式變更控制項的 DPI 設定或表單發生時。
- <xref:System.Windows.Forms.Form.DpiChanged>其中目前顯示表單的顯示裝置上的 DPI 設定變更時引發。

## <a name="new-helper-methods-and-properties"></a>新的協助程式方法和屬性

.NET Framework 4.7 也新增了許多新的協助程式方法和屬性提供的 DPI 縮放比例的相關資訊，可讓您執行 DPI 縮放比例。 它們包括：

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>其中會將值從邏輯裝置像素為單位。

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>這會調整邏輯裝置的 DPI 點陣圖影像。

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>它會傳回目前裝置的 DPI。

## <a name="versioning-considerations"></a>版本控制考量

除了.NET Framework 4.7 和 Windows 10 Creators Update 上執行，它不相容於高 DPI 的改進功能環境也可能會執行您的應用程式。 在此情況下，您必須開發您的應用程式的後援。 您可以執行[自訂繪圖](./controls/user-drawn-controls.md)來處理調整。

若要這樣做，您也需要判斷您的應用程式執行所在的作業系統。 您可以使用如下所示的程式碼來這麼做：

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

請注意您的應用程式將不會成功地偵測 Windows 10 是否未列出為支援的作業系統，應用程式資訊清單中。

您也可以檢查應用程式建置的.NET framework 版本：

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>另請參閱

- [Windows Form 加入組態項目](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [調整 Windows Forms 的大小和比例](adjusting-the-size-and-scale-of-windows-forms.md)
