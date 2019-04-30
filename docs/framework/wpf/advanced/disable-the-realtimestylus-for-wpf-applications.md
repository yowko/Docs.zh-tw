---
title: 停用 WPF 應用程式的 RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: e44b71ac5af64ab3a6cb008db71e5a8881592e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962486"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="29974-102">停用 WPF 應用程式的 RealTimeStylus</span><span class="sxs-lookup"><span data-stu-id="29974-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="29974-103">Windows Presentation Foundation (WPF) 已內建支援來處理 Windows 7 具備觸控輸入。支援是透過平板電腦平台的即時手寫筆輸入<xref:System.Windows.UIElement.OnStylusDown%2A>， <xref:System.Windows.UIElement.OnStylusUp%2A>，和<xref:System.Windows.UIElement.OnStylusMove%2A>事件。</span><span class="sxs-lookup"><span data-stu-id="29974-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="29974-104">Windows 7 也會提供 Win32 WM_TOUCH 視窗訊息的多點觸控輸入。</span><span class="sxs-lookup"><span data-stu-id="29974-104">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="29974-105">這兩個 Api 互斥上相同的 HWND。</span><span class="sxs-lookup"><span data-stu-id="29974-105">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="29974-106">啟用觸控輸入透過平板電腦平台 （WPF 應用程式的預設值） 會停用 WM_TOUCH 訊息。</span><span class="sxs-lookup"><span data-stu-id="29974-106">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="29974-107">如此一來，用於接收來自 WPF 視窗的觸控訊息 WM_TOUCH，您必須停用在 WPF 中的內建的手寫筆支援。</span><span class="sxs-lookup"><span data-stu-id="29974-107">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="29974-108">這是適用的案例，例如裝載使用 WM_TOUCH 的元件，為 WPF 視窗中。</span><span class="sxs-lookup"><span data-stu-id="29974-108">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="29974-109">若要停用 WPF 接聽手寫筆輸入，移除任何新增的 WPF 視窗的平板電腦支援。</span><span class="sxs-lookup"><span data-stu-id="29974-109">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29974-110">範例</span><span class="sxs-lookup"><span data-stu-id="29974-110">Example</span></span>  
 <span data-ttu-id="29974-111">下列範例程式碼示範如何使用反映來移除預設平板電腦平台支援。</span><span class="sxs-lookup"><span data-stu-id="29974-111">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="29974-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29974-112">See also</span></span>

- [<span data-ttu-id="29974-113">攔截手寫筆的輸入</span><span class="sxs-lookup"><span data-stu-id="29974-113">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
