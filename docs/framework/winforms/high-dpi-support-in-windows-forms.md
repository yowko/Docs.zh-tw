---
title: "在 Windows Form 中的高 DPI 支援"
ms.custom: 
ms.date: 05/16/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2461c507c0d2a27f1c2bdfe85327d11318b17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="high-dpi-support-in-windows-forms"></a>在 Windows Form 中的高 DPI 支援

從.NET Framework 4.7 開始，Windows Form 包含常見的高 DPI 與動態 DPI 情節的增強功能。 這些活動包括： 

- 改良的縮放比例和 Windows Form 的數字的版面配置控制項，例如<xref:System.Windows.Forms.MonthCalendar>控制項和<xref:System.Windows.Forms.CheckedListBox>控制項。 

- 單次縮放比例。  在 .NET Framework 4.6 及更早版本，透過多個行程，這會造成部分控制項，以調整多個必要執行縮放比例。

- 支援動態 DPI 案例，已啟動的 Windows Form 應用程式之後變更 DPI 或小數位數因素的使用者。

在.NET Framework 4.7 為開頭的.NET framework 版本中，增強高 DPI 支援是選擇性功能。 您必須設定您的應用程式利用.net framework。

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a>設定您的 Windows Form 應用程式的高 DPI 支援

支援高 DPI 感知的新 Windows Form 功能是僅適用於目標.NET Framework 4.7 和開頭為 Windows 10 建立者更新的 Windows 作業系統上執行的應用程式。 

此外，若要設定高 DPI 支援在 Windows Form 應用程式中，您必須執行下列動作：

- 宣告與 Windows 10 的相容性。

  若要這樣做，請加入下列程式資訊清單檔案：

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.comn:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- 啟用每個監視 DPI 感知*app.config*檔案。

  Windows Form 導入了新[ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md)元素來支援新功能和自訂加入開頭為.NET Framework 4.7。 若要充分利用支援高 DPI 的新功能，加上下列應用程式組態檔。   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > 在舊版的.NET Framework 中，您會使用資訊清單加入高 DPI 支援。 不建議這種方法，因為它會覆寫 app.config 檔案中所定義的設定。
   
- 呼叫靜態<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法。
   
  這應該是第一個方法呼叫您的應用程式進入點。 例如: 
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a>選擇退出個別的高 DPI 功能

設定`DpiAwareness`值設定為`PerMonitorV2`可讓從.NET Framework 4.7 的.NET Framework 版本所支援的所有高 DPI 感知功能。 一般而言，這樣已足夠大多數的 Windows Form 應用程式。 不過，您可以選擇不使用一或多個個別的功能。 執行此作業最重要的原因是現有的應用程式程式碼已經處理該功能。  比方說，如果您的應用程式會處理自動調整，您可能想要停用自動調整大小功能，如下所示：

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

如需個別的索引鍵和其值的清單，請參閱[Windows Form 加入組態項目](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)。

## <a name="new-dpi-change-events"></a>新的 DPI 變更事件

從.NET Framework 4.7 開始，三個新的事件可讓您以程式設計方式處理動態 DPI 變更：

- <xref:System.Windows.Forms.Control.DpiChangedAfterParent>它的父控制項的 DPI 變更事件之後以程式設計方式變更控制項的 DPI 設定或表單發生時引發的。
- <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>其父控制項的 DPI 變更事件之前以程式設計方式變更控制項的 DPI 設定或表單發生時引發的。
- <xref:System.Windows.Forms.Form.DpiChanged>其中顯示裝置目前顯示表單上的 DPI 設定變更時引發。

## <a name="new-helper-methods-and-properties"></a>新的協助程式方法和屬性

.NET Framework 4.7 也會加入許多新的 helper 方法和屬性，提供 DPI 縮放比例的相關資訊，讓您執行 DPI 縮放比例。 這些活動包括：

- <xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>可將值從邏輯轉換成裝置像素為單位。

- <xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>其中縮放邏輯裝置的 DPI 點陣圖影像。

- <xref:System.Windows.Forms.Control.DeviceDpi%2A>它會傳回目前裝置 DPI。

## <a name="versioning-considerations"></a>版本控制的考量

除了.NET Framework 4.7 和 Windows 10 建立者的更新版上執行，應用程式也可能以不相容高 DPI 的增強功能的環境中執行。 在此情況下，您必須開發應用程式的後援。 您可以執行[自訂繪圖](./controls/user-drawn-controls.md)處理縮放比例。

若要這樣做，您也需要判斷您的應用程式執行所在的作業系統。 您可以執行，具有類似下列程式碼：

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

請注意，您的應用程式不會成功偵測到 Windows 10 是否未列出為支援的作業系統，應用程式資訊清單中。

您也可以檢查應用程式建置時執行的.NET framework 版本：

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a>請參閱

[Windows Form 加入組態項目](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[調整 Windows Forms 的大小和比例](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
