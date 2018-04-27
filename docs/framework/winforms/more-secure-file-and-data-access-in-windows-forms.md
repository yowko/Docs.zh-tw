---
title: Windows Form 中更安全的檔案和資料存取
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 77c69c5c39d90dcc28aa9c6084d84ace29df6f18
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="4e1e9-102">Windows Form 中更安全的檔案和資料存取</span><span class="sxs-lookup"><span data-stu-id="4e1e9-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="4e1e9-103">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 使用權限協助保護資源與資料。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uses permissions to help protect resources and data.</span></span> <span data-ttu-id="4e1e9-104">您的應用程式可以讀取或寫入資料的位置取決於應用程式授與權限。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="4e1e9-105">當您的應用程式在部分信任的環境中執行時，您可能無法存取您的資料，或者您可能要改變您存取資料的方式。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="4e1e9-106">當您遇到安全性限制時，您有兩個選項：判斷權限 (假設已授與您的應用程式)，或者使用被寫成具有在部分信任環境運作功能的版本。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="4e1e9-107">下列章節將討論如何使用在部分信任環境執行的應用程式所產生的檔案、資料庫以及登錄存取。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e1e9-108">根據預設，產生 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署的工具預設這些部署去要求來自執行那些程式之電腦的完全信任。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-108">By default, tools that generate [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="4e1e9-109">如果您決定您想要在部分信任中執行的額外的安全性優點，您必須變更此預設值，在 Visual Studio 或其中一個[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]工具 （Mage.exe 或 MageUI.exe）。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="4e1e9-110">如需有關 Windows Forms 安全性，以及如何判斷您的應用程式的適當信任層級的詳細資訊，請參閱[安全性的 Windows Form 概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](../../../docs/framework/winforms/security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="4e1e9-111">檔案存取</span><span class="sxs-lookup"><span data-stu-id="4e1e9-111">File Access</span></span>  
 <span data-ttu-id="4e1e9-112"><xref:System.Security.Permissions.FileIOPermission> 類別控制在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的檔案與資料夾存取。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="4e1e9-113">根據預設，安全性系統並未將 <xref:System.Security.Permissions.FileIOPermission> 授與部分安全性環境，例如近端內部網路或者網際網路區域。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="4e1e9-114">然而，如果您修改您應用程式的設計或使用不同方法來存取檔案，需要檔案存取的應用程式依然能夠在這些環境中運作。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="4e1e9-115">根據預設，近端內部網路區域已經被授與權限能夠存取相同網站與相同目錄、連線到網站的原始來源、以及從其安裝目錄讀取。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="4e1e9-116">根據預設，網際網路區域只被授與連回其原始網站的權限。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="4e1e9-117">使用者指定的檔案</span><span class="sxs-lookup"><span data-stu-id="4e1e9-117">User-Specified Files</span></span>  
 <span data-ttu-id="4e1e9-118">沒有檔案存取權限的處理方法之一是使用 <xref:System.Windows.Forms.OpenFileDialog> 或 <xref:System.Windows.Forms.SaveFileDialog> 類別來提示使用者提供特定的檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="4e1e9-119">這種使用者互動有助於提供在某種程度上保證應用程式無法惡意載入私人檔案或覆寫重要檔案。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="4e1e9-120"><xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 與 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法，藉著開啟使用者指定的檔案資料流來提供讀取與寫入的檔案存取。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="4e1e9-121">本方法也藉由模糊檔案路徑來協助保護使用者的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e1e9-122">這些權限會根據您的應用程式是在網際網路區域或內部網路區域而有所不同。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="4e1e9-123">網際網路區域應用程式只能使用 <xref:System.Windows.Forms.OpenFileDialog>，而內部網路應用程式擁有不受限制的檔案對話方塊使用權限。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="4e1e9-124"><xref:System.Security.Permissions.FileDialogPermission> 類別會指定您的應用程式能夠使用哪一種對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="4e1e9-125">下列表格顯示在您要使用每一種 <xref:System.Windows.Forms.FileDialog> 類別時必需要有的值 。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="4e1e9-126">類別</span><span class="sxs-lookup"><span data-stu-id="4e1e9-126">Class</span></span>|<span data-ttu-id="4e1e9-127">必需的存取值</span><span class="sxs-lookup"><span data-stu-id="4e1e9-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  <span data-ttu-id="4e1e9-128">特定的權限在方法 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 真的被呼叫之前不會被要求。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="4e1e9-129">顯示檔案對話方塊的權限不會授與您的應用程式對 <xref:System.Windows.Forms.FileDialog>、<xref:System.Windows.Forms.OpenFileDialog> 與 <xref:System.Windows.Forms.SaveFileDialog> 類別所有成員的完整存取權。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="4e1e9-130">要了解呼叫每一種方法所需要的確切權限，請參閱 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 類別程式庫文件中該方法的參考主題。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-130">For the exact permissions that are required to call each method, see the reference topic for that method in the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] class library documentation.</span></span>  
  
 <span data-ttu-id="4e1e9-131">下列程式碼範例使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法，來將使用者指定的檔案開啟至 <xref:System.Windows.Forms.RichTextBox> 控制項。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="4e1e9-132">這個範例需要 <xref:System.Security.Permissions.FileDialogPermission> 以及相關的列舉值 <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="4e1e9-133">此範例示範如何處理 <xref:System.Security.SecurityException> 來判斷是否應該停用儲存功能。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="4e1e9-134">這個範例需要您的 <xref:System.Windows.Forms.Form> 有 <xref:System.Windows.Forms.Button> 控制項命名為 `ButtonOpen`，和 <xref:System.Windows.Forms.RichTextBox> 控制項命名為 `RtfBoxMain`。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e1e9-135">範例中不會顯示儲存功能的程式設計邏輯。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="4e1e9-136">在 Visual C# 中，請確定您加入程式碼，讓事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="4e1e9-137">藉由使用前一個範例的程式碼，下列程式碼會示範如何啟用事件處理常式。`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="4e1e9-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="4e1e9-138">其他檔案</span><span class="sxs-lookup"><span data-stu-id="4e1e9-138">Other Files</span></span>  
 <span data-ttu-id="4e1e9-139">有時候，您必須讀取或寫入使用者未指定的檔案，例如當您必須保存應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="4e1e9-140">在近端內部網路和網際網路區域中，您的應用程式將不會有把資料儲存在本機檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="4e1e9-141">但是您的應用程式可以將資料儲存在隔離儲存區。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="4e1e9-142">隔離儲存區是抽象的資料區間 (不是特定的儲存位置)，其中包含一或多個稱為存放區的隔離儲存區，存放區包含儲存資料的實際目錄位置。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="4e1e9-143">檔案存取權限，例如 <xref:System.Security.Permissions.FileIOPermission> 並非必要項；相反地， <xref:System.Security.Permissions.IsolatedStoragePermission> 類別控制隔離儲存區的權限。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="4e1e9-144">根據預設，在近端內部網路和網際網路區域執行的應用程式可以使用隔離儲存區來儲存資料。不過，像是磁碟配額之類的設定可能會有所不同。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="4e1e9-145">如需隔離儲存區的詳細資訊，請參閱[隔離儲存區](../../../docs/standard/io/isolated-storage.md)。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-145">For more information about isolated storage, see [Isolated Storage](../../../docs/standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="4e1e9-146">下列範例會使用隔離儲存區，將資料寫入存放區中的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="4e1e9-147">這個範例需要 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 以及  <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>  列舉值。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="4e1e9-148">此範例示範讀取和寫入 <xref:System.Windows.Forms.Button> 控制項的特定屬性值到隔離儲存區中的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="4e1e9-149">應用程式啟動之後就會呼叫  `Read` 函式，並且會在結束前呼叫 `Write` 函式。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="4e1e9-150">這個範例需要`Read`和`Write`函式為成員的存在<xref:System.Windows.Forms.Form>包含<xref:System.Windows.Forms.Button>控制項，名為`MainButton`。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a><span data-ttu-id="4e1e9-151">資料庫存取</span><span class="sxs-lookup"><span data-stu-id="4e1e9-151">Database Access</span></span>  
 <span data-ttu-id="4e1e9-152">存取資料庫所需的權限因資料庫提供者而異；不過，只有以適當權限來執行的應用程式可以透過資料連接存取資料庫。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="4e1e9-153">如需存取資料庫所需的權限的詳細資訊，請參閱[程式碼存取安全性和 ADO.NET](../../../docs/framework/data/adonet/code-access-security.md)。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../../../docs/framework/data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="4e1e9-154">如果您因為希望在部分信任中執行您的應用程式而無法直接存取資料庫，您可以使用 Web 服務做為替代方式來存取您的資料。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="4e1e9-155">Web 服務是一種可透過網路以程式設計方式存取的軟體。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="4e1e9-156">透過 Web 服務，應用程式可以在程式碼群組區域之間分享資料。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="4e1e9-157">根據預設，近端內部網路和網際網路區域中的應用程式會被授與權限來存取他們的來源網站，讓他們能夠呼叫相同的伺服器上裝載的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="4e1e9-158">如需詳細資訊，請參閱[ASP.NET AJAX 中的 Web 服務](http://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b)或[Windows Communication Foundation](http://msdn.microsoft.com/library/ms735119.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-158">For more information see [Web Services in ASP.NET AJAX](http://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b) or [Windows Communication Foundation](http://msdn.microsoft.com/library/ms735119.aspx).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="4e1e9-159">登錄存取</span><span class="sxs-lookup"><span data-stu-id="4e1e9-159">Registry Access</span></span>  
 <span data-ttu-id="4e1e9-160"><xref:System.Security.Permissions.RegistryPermission> 類別控制作業系統登錄的存取權。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="4e1e9-161">根據預設，只有在本機執行的應用程式可以存取登錄。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="4e1e9-162"><xref:System.Security.Permissions.RegistryPermission> 只授與應用程式嘗試登錄存取；它並不保證存取將會成功，因為作業系統仍然會強制執行登錄上的安全性。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="4e1e9-163">因為您無法在部分信任下存取登錄，您可能需要尋找儲存資料的其他方法。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="4e1e9-164">當您儲存應用程式設定時，使用隔離儲存區，而不是登錄。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="4e1e9-165">隔離儲存區也可以用來儲存其他應用程式特定的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="4e1e9-166">您也可以儲存與伺服器或來源網站相關的全域應用程式資訊，因為根據預設，應用程式被授與存取其來源網站的權限。</span><span class="sxs-lookup"><span data-stu-id="4e1e9-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e1e9-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e1e9-167">See Also</span></span>  
 [<span data-ttu-id="4e1e9-168">Windows Forms 中更安全的列印</span><span class="sxs-lookup"><span data-stu-id="4e1e9-168">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [<span data-ttu-id="4e1e9-169">Windows Forms 中的其他安全性考量</span><span class="sxs-lookup"><span data-stu-id="4e1e9-169">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [<span data-ttu-id="4e1e9-170">Windows Forms 中的安全性概觀</span><span class="sxs-lookup"><span data-stu-id="4e1e9-170">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [<span data-ttu-id="4e1e9-171">Windows Forms 安全性</span><span class="sxs-lookup"><span data-stu-id="4e1e9-171">Windows Forms Security</span></span>](../../../docs/framework/winforms/windows-forms-security.md)  
 [<span data-ttu-id="4e1e9-172">Mage.exe (資訊清單產生和編輯工具)</span><span class="sxs-lookup"><span data-stu-id="4e1e9-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [<span data-ttu-id="4e1e9-173">MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)</span><span class="sxs-lookup"><span data-stu-id="4e1e9-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
