---
title: 停用 WPF 應用程式的 RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: acae177e1c49a6a1161bcf48f8e2e8ac1bfe13b8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991848"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="a07b3-102">停用 WPF 應用程式的 RealTimeStylus</span><span class="sxs-lookup"><span data-stu-id="a07b3-102">Disable the RealTimeStylus for WPF Applications</span></span>
<span data-ttu-id="a07b3-103">Windows Presentation Foundation （WPF）內建支援處理 Windows 7 觸控輸入。</span><span class="sxs-lookup"><span data-stu-id="a07b3-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="a07b3-104">支援是透過 tablet 平臺的即時手寫筆輸入，做為<xref:System.Windows.UIElement.OnStylusDown%2A>、 <xref:System.Windows.UIElement.OnStylusUp%2A>和<xref:System.Windows.UIElement.OnStylusMove%2A>事件。</span><span class="sxs-lookup"><span data-stu-id="a07b3-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="a07b3-105">Windows 7 也提供多點觸控輸入作為 Win32 WM_TOUCH 視窗訊息。</span><span class="sxs-lookup"><span data-stu-id="a07b3-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="a07b3-106">這兩個 Api 在相同的 HWND 上是互斥的。</span><span class="sxs-lookup"><span data-stu-id="a07b3-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="a07b3-107">透過 tablet 平臺啟用觸控輸入（WPF 應用程式的預設值）會停用 WM_TOUCH 訊息。</span><span class="sxs-lookup"><span data-stu-id="a07b3-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="a07b3-108">因此，若要使用 WM_TOUCH 從 WPF 視窗接收觸控訊息，您必須停用 WPF 中的內建手寫筆支援。</span><span class="sxs-lookup"><span data-stu-id="a07b3-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="a07b3-109">這適用于裝載使用 WM_TOUCH 之元件的 WPF 視窗這類案例。</span><span class="sxs-lookup"><span data-stu-id="a07b3-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="a07b3-110">若要停用 WPF 接聽手寫筆輸入，請移除 WPF 視窗所加入的任何平板電腦支援。</span><span class="sxs-lookup"><span data-stu-id="a07b3-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a07b3-111">範例</span><span class="sxs-lookup"><span data-stu-id="a07b3-111">Example</span></span>  
 <span data-ttu-id="a07b3-112">下列範例程式碼示範如何使用反映來移除預設的平板電腦平臺支援。</span><span class="sxs-lookup"><span data-stu-id="a07b3-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a07b3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a07b3-113">See also</span></span>

- [<span data-ttu-id="a07b3-114">攔截手寫筆的輸入</span><span class="sxs-lookup"><span data-stu-id="a07b3-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
