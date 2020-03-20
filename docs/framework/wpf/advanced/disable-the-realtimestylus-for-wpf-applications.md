---
title: 禁用即時樣式
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: c2500b494f76c85e4b23823a44a180d85d5092ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186076"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="dd4d0-102">停用 WPF 應用程式的 RealTimeStylus</span><span class="sxs-lookup"><span data-stu-id="dd4d0-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="dd4d0-103">Windows 演示基礎 （WPF） 已內置了用於處理 Windows 7 觸摸輸入的支援。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="dd4d0-104">支援來自平板電腦平臺的即時手寫筆輸入，如<xref:System.Windows.UIElement.OnStylusDown%2A>、<xref:System.Windows.UIElement.OnStylusUp%2A>和<xref:System.Windows.UIElement.OnStylusMove%2A>事件。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="dd4d0-105">Windows 7 還提供多點觸控輸入，作為 Win32 WM_TOUCH視窗消息。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="dd4d0-106">這兩個 API 在同一 HWND 上是互斥的。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="dd4d0-107">通過平板電腦平臺啟用觸摸輸入（WPF 應用程式的預設值）可禁用WM_TOUCH消息。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="dd4d0-108">因此，要使用WM_TOUCH接收來自 WPF 視窗的觸摸消息，必須禁用 WPF 中的內置手寫筆支援。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="dd4d0-109">這適用于使用WM_TOUCH的元件的 WPF 視窗等方案。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="dd4d0-110">要禁用 WPF 偵聽手寫筆輸入，請刪除 WPF 視窗添加的任何平板電腦支援。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd4d0-111">範例</span><span class="sxs-lookup"><span data-stu-id="dd4d0-111">Example</span></span>  
 <span data-ttu-id="dd4d0-112">以下示例代碼演示如何使用反射刪除預設的平板電腦平臺支援。</span><span class="sxs-lookup"><span data-stu-id="dd4d0-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd4d0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd4d0-113">See also</span></span>

- [<span data-ttu-id="dd4d0-114">攔截手寫筆的輸入</span><span class="sxs-lookup"><span data-stu-id="dd4d0-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
