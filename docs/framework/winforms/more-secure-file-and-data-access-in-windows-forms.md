---
title: "Windows Form 中更安全的檔案和資料存取 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料 [Windows Form], 安全存取"
  - "資料存取 [Windows Form]"
  - "資料庫存取 (Windows Form 安全性)"
  - "檔案存取 [Windows Form]"
  - "登錄 [Windows Form]"
  - "安全性 [Windows Form], 資料存取"
  - "安全性 [Windows Form], 檔案存取"
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Windows Form 中更安全的檔案和資料存取
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 使用權限協助保護資源與資料。  您的應用程式可以讀取或寫入資料的位置取決於應用程式授與權限。  當您的應用程式在部分信任的環境中執行時，您可能無法存取您的資料，或者您可能要改變您存取資料的方式。  
  
 當您遇到安全性限制時，您有兩個選項：判斷權限 \(假設已授與您的應用程式\)，或者使用被寫成具有在部分信任環境運作功能的版本。  下列章節將討論如何使用在部分信任環境執行的應用程式所產生的檔案、資料庫以及登錄存取。  
  
> [!NOTE]
>  根據預設，產生 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] 部署的工具預設這些部署去要求來自執行那些程式之電腦的完全信任。  如果您決定想要執行於部分信任中的額外安全性優點，您必須在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 或 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 下列工具\(Mage.exe 或 MageUI.exe\) 中改變這項預設值。   如需 Windows Forms 安全性，以及如何為您的應用程式判斷適當信任層級的詳細資訊，請參閱  [Windows Form 中的安全性概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)。  
  
## 檔案存取  
 <xref:System.Security.Permissions.FileIOPermission> 類別控制在 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 中的檔案與資料夾存取。  根據預設，安全性系統並未將 <xref:System.Security.Permissions.FileIOPermission> 授與部分安全性環境，例如近端內部網路或者網際網路區域。  然而，如果您修改您應用程式的設計或使用不同方法來存取檔案，需要檔案存取的應用程式依然能夠在這些環境中運作。  根據預設，近端內部網路區域已經被授與權限能夠存取相同網站與相同目錄、連線到網站的原始來源、以及從其安裝目錄讀取。  根據預設，網際網路區域只被授與連回其原始網站的權限。  
  
### 使用者指定的檔案  
 沒有檔案存取權限的處理方法之一是使用 <xref:System.Windows.Forms.OpenFileDialog> 或 <xref:System.Windows.Forms.SaveFileDialog> 類別來提示使用者提供特定的檔案資訊。  這種使用者互動有助於提供在某種程度上保證應用程式無法惡意載入私人檔案或覆寫重要檔案。  <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 與 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法，藉著開啟使用者指定的檔案資料流來提供讀取與寫入的檔案存取。  本方法也藉由模糊檔案路徑來協助保護使用者的檔案。  
  
> [!NOTE]
>  這些權限會根據您的應用程式是在網際網路區域或內部網路區域而有所不同。  網際網路區域應用程式只能使用 <xref:System.Windows.Forms.OpenFileDialog>，而內部網路應用程式擁有不受限制的檔案對話方塊使用權限。  
  
 <xref:System.Security.Permissions.FileDialogPermission> 類別會指定您的應用程式能夠使用哪一種對話方塊。  下列表格顯示在您要使用每一種 <xref:System.Windows.Forms.FileDialog> 類別時必需要有的值 。  
  
|類別|必需的存取值|  
|--------|------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess>|  
  
> [!NOTE]
>  特定的權限在方法 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 真的被呼叫之前不會被要求。  
  
 顯示檔案對話方塊的權限不會授與您的應用程式對 <xref:System.Windows.Forms.FileDialog>、<xref:System.Windows.Forms.OpenFileDialog> 與 <xref:System.Windows.Forms.SaveFileDialog> 類別所有成員的完整存取權。  要了解呼叫每一種方法所需要的確切權限，請參閱 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 類別程式庫文件中該方法的參考主題。  
  
 下列程式碼範例使用 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法，來將使用者指定的檔案開啟至 <xref:System.Windows.Forms.RichTextBox> 控制項。  這個範例需要 <xref:System.Security.Permissions.FileDialogPermission> 以及相關的列舉值 <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> 。  此範例示範如何處理 <xref:System.Security.SecurityException> 來判斷是否應該停用儲存功能。  這個範例需要您的 <xref:System.Windows.Forms.Form> 有 <xref:System.Windows.Forms.Button> 控制項命名為 `ButtonOpen`，和 <xref:System.Windows.Forms.RichTextBox> 控制項命名為 `RtfBoxMain`。  
  
> [!NOTE]
>  範例中不會顯示儲存功能的程式設計邏輯。  
  
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
>  在 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] 中，請確定您加入程式碼來啟用事件處理常式。  藉由使用前一個範例的程式碼，下列程式碼會示範如何啟用事件處理常式。`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### 其他檔案  
 有時候，您必須讀取或寫入使用者未指定的檔案，例如當您必須保存應用程式設定。  在近端內部網路和網際網路區域中，您的應用程式將不會有把資料儲存在本機檔案的權限。  但是您的應用程式可以將資料儲存在隔離儲存區。  隔離儲存區是抽象的資料區間 \(不是特定的儲存位置\)，其中包含一或多個稱為存放區的隔離儲存區，存放區包含儲存資料的實際目錄位置。  檔案存取權限，例如 <xref:System.Security.Permissions.FileIOPermission> 並非必要項；相反地， <xref:System.Security.Permissions.IsolatedStoragePermission> 類別控制隔離儲存區的權限。  根據預設，在近端內部網路和網際網路區域執行的應用程式可以使用隔離儲存區來儲存資料。不過，像是磁碟配額之類的設定可能會有所不同。  如需隔離儲存區的詳細資訊，請參閱[隔離儲存區](../../../docs/standard/io/isolated-storage.md)。  
  
 下列範例會使用隔離儲存區，將資料寫入存放區中的檔案。  這個範例需要 <xref:System.Security.Permissions.IsolatedStorageFilePermission> 以及  <xref:System.Security.Permissions.IsolatedStorageContainment> 列舉值。  此範例示範讀取和寫入 <xref:System.Windows.Forms.Button> 控制項的特定屬性值到隔離儲存區中的檔案。  應用程式啟動之後就會呼叫  `Read` 函式，並且會在結束前呼叫 `Write` 函式。  這個範例需要 `Read` 與 `Write` 函式做為成員存在於 <xref:System.Windows.Forms.Form>，而包含 <xref:System.Windows.Forms.Button> 被名為 `MainButton` 的   控制項。  
  
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
  
## 資料庫存取  
 存取資料庫所需的權限因資料庫提供者而異；不過，只有以適當權限來執行的應用程式可以透過資料連接存取資料庫。  如需存取資料庫所需之權限的詳細資訊，請參閱 [程式碼存取安全性和 ADO.NET](../../../docs/framework/data/adonet/code-access-security.md)。  
  
 如果您因為希望在部分信任中執行您的應用程式而無法直接存取資料庫，您可以使用 Web 服務做為替代方式來存取您的資料。  Web 服務是一種可透過網路以程式設計方式存取的軟體。  透過 Web 服務，應用程式可以在程式碼群組區域之間分享資料。  根據預設，近端內部網路和網際網路區域中的應用程式會被授與權限來存取他們的來源網站，讓他們能夠呼叫相同的伺服器上裝載的 Web 服務。  如需詳細資訊，請參閱 [ASP.NET AJAX 中的 Web 服務](http://msdn.microsoft.com/zh-tw/8290e543-7eff-47a4-aace-681f3c07229b)或 [Windows Communication Foundation](http://msdn.microsoft.com/library/ms735119.aspx)。  
  
## 登錄存取  
 <xref:System.Security.Permissions.RegistryPermission> 類別控制作業系統登錄的存取權。  根據預設，只有在本機執行的應用程式可以存取登錄。  <xref:System.Security.Permissions.RegistryPermission> 只授與應用程式嘗試登錄存取；它並不保證存取將會成功，因為作業系統仍然會強制執行登錄上的安全性。  
  
 因為您無法在部分信任下存取登錄，您可能需要尋找儲存資料的其他方法。  當您儲存應用程式設定時，使用隔離儲存區，而不是登錄。  隔離儲存區也可以用來儲存其他應用程式特定的檔案。  您也可以儲存與伺服器或來源網站相關的全域應用程式資訊，因為根據預設，應用程式被授與存取其來源網站的權限。  
  
## 請參閱  
 [Windows Form 中更安全的列印](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)   
 [Windows Form 中的其他安全性考量](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)   
 [Windows Form 中的安全性概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)   
 [Windows Form 安全性](../../../docs/framework/winforms/windows-forms-security.md)   
 [Mage.exe \(資訊清單產生和編輯工具\)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)