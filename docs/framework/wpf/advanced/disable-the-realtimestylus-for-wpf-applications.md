---
title: 停用 WPF 應用程式的 RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 6af7ff3addfe2673ab73ff0f977770f89c6234bb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371122"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>停用 WPF 應用程式的 RealTimeStylus
Windows Presentation Foundation (WPF) 已內建支援來處理 Windows 7 具備觸控輸入。支援是透過平板電腦平台的即時手寫筆輸入<xref:System.Windows.UIElement.OnStylusDown%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>，和<xref:System.Windows.UIElement.OnStylusMove%2A>事件。 Windows 7 也會提供 Win32 WM_TOUCH 視窗訊息的多點觸控輸入。 這兩個 Api 互斥上相同的 HWND。 啟用觸控輸入透過平板電腦平台 （WPF 應用程式的預設值） 會停用 WM_TOUCH 訊息。 如此一來，用於接收來自 WPF 視窗的觸控訊息 WM_TOUCH，您必須停用在 WPF 中的內建的手寫筆支援。 這是適用的案例，例如裝載使用 WM_TOUCH 的元件，為 WPF 視窗中。  
  
 若要停用 WPF 接聽手寫筆輸入，移除任何新增的 WPF 視窗的平板電腦支援。  
  
## <a name="example"></a>範例  
 下列範例程式碼示範如何使用反映來移除預設平板電腦平台支援。  
  
```  
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
