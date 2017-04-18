---
title: "停用 WPF 應用程式的 RealTimeStylus | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 停用 WPF 應用程式的 RealTimeStylus
Windows Presentation Foundation \(WPF\) 擁有處理 Windows 7 觸控輸入的內建支援。這項支援是透過 Tablet 平台的即時手寫筆輸入當做 <xref:System.Windows.UIElement.OnStylusDown%2A>、<xref:System.Windows.UIElement.OnStylusUp%2A> 和 <xref:System.Windows.UIElement.OnStylusMove%2A> 事件提供。  此外，Windows 7 還提供多點觸控輸入做為 Win32 WM\_TOUCH 視窗訊息。  這兩種 API 在相同 HWND 上是互斥的。  透過 Tablet 平台 \(WPF 應用程式的預設值\) 啟用觸控輸入會停用 WM\_TOUCH 訊息。  因此，若要使用 WM\_TOUCH 接收來自 WPF 視窗的觸控訊息，您必須停用 WPF 中內建的手寫筆支援。  這種情況適用於 WPF 視窗裝載使用 WM\_TOUCH 的元件這類情節。  
  
 若要停用 WPF 接聽手寫筆輸入的功能，請移除 WPF 視窗加入的任何 Tablet 支援。  
  
## 範例  
 下列範例程式碼會顯示如何使用反映移除預設的 Tablet 平台支援。  
  
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
  
## 請參閱  
 [攔截手寫筆的輸入](../../../../docs/framework/wpf/advanced/intercepting-input-from-the-stylus.md)