---
title: 停用 RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 74145c32af7e9ebbc774a0301e205aa1eb1539b3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737947"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>停用 WPF 應用程式的 RealTimeStylus

Windows Presentation Foundation （WPF）內建支援處理 Windows 7 觸控輸入。 支援是透過 tablet 平臺的即時手寫筆輸入，做為 <xref:System.Windows.UIElement.OnStylusDown%2A>、<xref:System.Windows.UIElement.OnStylusUp%2A>和 <xref:System.Windows.UIElement.OnStylusMove%2A> 事件。 Windows 7 也提供多點觸控輸入做為 Win32 WM_TOUCH 視窗訊息。 這兩個 Api 在相同的 HWND 上是互斥的。 透過 tablet 平臺啟用觸控輸入（WPF 應用程式的預設值）會停用 WM_TOUCH 訊息。 因此，若要使用 WM_TOUCH 從 WPF 視窗接收觸控訊息，您必須停用 WPF 內建的手寫筆支援。 這適用于裝載使用 WM_TOUCH 之元件的 WPF 視窗這類案例。  
  
 若要停用 WPF 接聽手寫筆輸入，請移除 WPF 視窗所加入的任何平板電腦支援。  
  
## <a name="example"></a>範例  
 下列範例程式碼示範如何使用反映來移除預設的平板電腦平臺支援。  
  
```csharp  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>另請參閱

- [攔截手寫筆的輸入](intercepting-input-from-the-stylus.md)
