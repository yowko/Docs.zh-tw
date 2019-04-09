---
title: HOW TO：設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: 6fa00c4ced8c05d056703560e5740689c6dcfe39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096286"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="f0b0c-102">HOW TO：設定 IIS 5.0 和 IIS 6.0 以部署 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="f0b0c-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="f0b0c-103">您可以從大多數網頁伺服器部署 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式，只要這些伺服器是以適當的 [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] 類型所設定。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] types.</span></span> <span data-ttu-id="f0b0c-104">根據預設，[!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] 是以這些 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型所設定，但 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 和 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] 則不是。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-104">By default, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] is configured with these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types, but [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] are not.</span></span>

<span data-ttu-id="f0b0c-105">本主題說明何設定 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 和 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]，以部署 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-105">This topic describes how to configure [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] and [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="f0b0c-106">您可以檢查*UserAgent*登錄，以判斷系統是否已安裝的.NET Framework 中的字串。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="f0b0c-107">詳細資料和指令碼，會檢查*UserAgent*字串，以判斷是否要在系統上安裝.NET Framework，請參閱[偵測是否安裝.NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="f0b0c-108">調整內容到期設定</span><span class="sxs-lookup"><span data-stu-id="f0b0c-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="f0b0c-109">您應該將內容到期設定調整為 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="f0b0c-110">下列程序概述如何使用 [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] 執行此作業。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-110">The following procedure outlines how to do this with [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span>

1. <span data-ttu-id="f0b0c-111">按一下 [開始] 功能表，指向 [系統管理工具]，然後按一下 [Internet Information Services (IIS) 管理員]。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="f0b0c-112">您也可以從命令列使用 "%SystemRoot%\system32\inetsrv\iis.msc" 來啟動此應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="f0b0c-113">展開 [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] 樹狀目錄，直到找到 [預設的網站] 節點。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-113">Expand the [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="f0b0c-114">以滑鼠右鍵按一下 [預設的網站]，然後從操作功能表選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="f0b0c-115">選取 [HTTP 標頭] 索引標籤，然後按一下 [啟用內容到期日]。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="f0b0c-116">設定內容於 1 分鐘後過期。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="f0b0c-117">註冊 MIME 類型和副檔名</span><span class="sxs-lookup"><span data-stu-id="f0b0c-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="f0b0c-118">您必須註冊數種 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型和副檔名，用戶端系統上的瀏覽器才能載入正確的處理常式。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-118">You must register several [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="f0b0c-119">您需要新增下列類型：</span><span class="sxs-lookup"><span data-stu-id="f0b0c-119">You need to add the following types:</span></span>

|<span data-ttu-id="f0b0c-120">副檔名</span><span class="sxs-lookup"><span data-stu-id="f0b0c-120">Extension</span></span>|<span data-ttu-id="f0b0c-121">MIME 類型</span><span class="sxs-lookup"><span data-stu-id="f0b0c-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="f0b0c-122">.manifest</span><span class="sxs-lookup"><span data-stu-id="f0b0c-122">.manifest</span></span>|<span data-ttu-id="f0b0c-123">application/manifest</span><span class="sxs-lookup"><span data-stu-id="f0b0c-123">application/manifest</span></span>|
|<span data-ttu-id="f0b0c-124">.xaml</span><span class="sxs-lookup"><span data-stu-id="f0b0c-124">.xaml</span></span>|<span data-ttu-id="f0b0c-125">application/xaml+xml</span><span class="sxs-lookup"><span data-stu-id="f0b0c-125">application/xaml+xml</span></span>|
|<span data-ttu-id="f0b0c-126">.application</span><span class="sxs-lookup"><span data-stu-id="f0b0c-126">.application</span></span>|<span data-ttu-id="f0b0c-127">application/x-ms-application</span><span class="sxs-lookup"><span data-stu-id="f0b0c-127">application/x-ms-application</span></span>|
|<span data-ttu-id="f0b0c-128">.xbap</span><span class="sxs-lookup"><span data-stu-id="f0b0c-128">.xbap</span></span>|<span data-ttu-id="f0b0c-129">application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="f0b0c-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="f0b0c-130">.deploy</span><span class="sxs-lookup"><span data-stu-id="f0b0c-130">.deploy</span></span>|<span data-ttu-id="f0b0c-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="f0b0c-131">application/octet-stream</span></span>|
|<span data-ttu-id="f0b0c-132">.xps</span><span class="sxs-lookup"><span data-stu-id="f0b0c-132">.xps</span></span>|<span data-ttu-id="f0b0c-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="f0b0c-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="f0b0c-134">您不需要在用戶端系統上註冊 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型或副檔名。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-134">You do not need to register [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types or file extensions on client systems.</span></span> <span data-ttu-id="f0b0c-135">當您安裝 Microsoft.NET Framework 時，它們會自動註冊。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="f0b0c-136">下列 Microsoft Visual Basic Scripting Edition (VBScript) 範例會自動新增必要[!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)]型別[!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types to [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].</span></span> <span data-ttu-id="f0b0c-137">若要使用指令碼，請將程式碼複製到伺服器上的 .vbs 檔案。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="f0b0c-138">然後，從命令列執行該檔案，或在 [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)] 中按兩下該檔案，以執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-138">Then, run the script by running the file from the command line or double-clicking the file in [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].</span></span>

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> <span data-ttu-id="f0b0c-139">多次執行此指令碼會在 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Metabase 中建立多個 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 對應項目。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-139">Running this script multiple times creates multiple [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] map entries in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

<span data-ttu-id="f0b0c-140">執行此指令碼之後，您可能不會從 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)] 看到其他 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-140">After you have run this script, you may not see additional [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types from the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)].</span></span> <span data-ttu-id="f0b0c-141">不過，這些 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型已新增至 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Metabase。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-141">However, these [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types have been added to the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span> <span data-ttu-id="f0b0c-142">下列指令碼會顯示 [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 或 [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] Metabase 中的所有 [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] 類型。</span><span class="sxs-lookup"><span data-stu-id="f0b0c-142">The following script will display all the [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] types in the [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] or [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase.</span></span>

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

<span data-ttu-id="f0b0c-143">請將指令碼儲存為 `.vbs` 檔案 (例如 `DiscoverIISMimeTypes.vbs`)，然後從命令提示字元使用下列命令來執行：</span><span class="sxs-lookup"><span data-stu-id="f0b0c-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
