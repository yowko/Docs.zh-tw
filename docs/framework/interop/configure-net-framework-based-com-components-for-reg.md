---
title: 作法：設定 .NET Framework 架構 COM 元件進行免註冊啟用
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b66265a58dcbb6f795e1d207e0bb6f75252161e
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093537"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a>作法：設定 .NET Framework 架構 COM 元件進行免註冊啟用
.NET Framework 型元件的免註冊啟用，只比 COM 元件的免註冊啟用略為複雜。 安裝程式需要兩個資訊清單：  
  
-   COM 應用程式必須有 Win32 樣式應用程式資訊清單，才能識別 Managed 元件。  
  
-   .NET Framework 元件必須具有執行階段所需啟用資訊的元件資訊清單。  
  
 本主題描述如何建立應用程式資訊清單與應用程式的關聯、建立元件資訊清單與元件的關聯，以及將元件資訊清單內嵌在組件中。  
  
### <a name="to-create-an-application-manifest"></a>建立應用程式資訊清單  
  
1.  使用 XML 編輯器，建立 (或修改) COM 應用程式所擁有的應用程式資訊清單，而其與一或多個 Managed 元件交互操作。  
  
2.  在檔案開頭，插入下列標準標頭：  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     如需資訊清單元素及其屬性的相關資訊，請參閱[應用程式資訊清單](/windows/desktop/SbsCs/application-manifests) \(英文\)。  
  
3.  識別資訊清單的擁有者。 在下列範例中，`myComApp` 第 1 版擁有資訊清單檔。  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  識別相依組件。 在下列範例中，`myComApp` 取決於 `myManagedComp`。  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="x86"   
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myManagedComp"   
                        version="6.0.0.0"   
                        processorArchitecture="X86"   
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5.  儲存並命名資訊清單檔。 應用程式資訊清單的名稱就是後接 .manifest 副檔名的組件可執行檔名稱。 例如，myComApp.exe 的應用程式資訊清單檔案名稱是 myComApp.exe.manifest。  
  
 您可以在與 COM 應用程式相同的目錄中安裝應用程式資訊清單。 或者，您可以將它當成資源新增至應用程式的.exe 檔案。 如需詳細資訊，請參閱[關於並存組件](/windows/desktop/SbsCs/about-side-by-side-assemblies-) \(英文\)。  
  
#### <a name="to-create-a-component-manifest"></a>建立元件資訊清單  
  
1.  使用 XML 編輯器，建立元件資訊清單以描述 Managed 組件。  
  
2.  在檔案開頭，插入下列標準標頭：  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  識別檔案的擁有者。 應用程式資訊清單檔中 `<dependentAssembly>` 項目的 `<assemblyIdentity>` 項目必須符合元件資訊清單中的項目。 在下列範例中，`myManagedComp` 版本 1.2.3.4 擁有資訊清單檔。  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  識別組件中的每個類別。 使用 `<clrClass>` 項目，唯一識別 Managed 組件中的每個類別。 項目 (即 `<assembly>` 項目的子項目) 具有下表所述的屬性。  
  
    |屬性|描述|必要|  
    |---------------|-----------------|--------------|  
    |`clsid`|指定要啟用之類別的識別碼。|是|  
    |`description`|通知使用者有關元件的字串。 空字串為預設值。|否|  
    |`name`|代表 Managed 類別的字串。|是|  
    |`progid`|要用於晚期繫結啟用的識別碼。|否|  
    |`threadingModel`|COM 執行緒模型。 「兩者」都是預設值。|否|  
    |`runtimeVersion`|指定要使用的 Common Language Runtime (CLR) 版本。 如果您未指定此屬性，而且尚未載入 CLR，則會載入具有 CLR 第 4 版前之最新已安裝 CLR 的元件。 如果您指定 v1.0.3705、v1.1.4322 或 v2.0.50727，版本會自動向前復原至 CLR 版本 4 之前的最新已安裝 CLR 版本 (通常是 v2.0.50727)。 如果已載入另一個版本的 CLR，並且可以透過並存同處理序方式載入指定的版本，則會載入指定的版本；否則，會使用載入的 CLR。 這可能會造成載入失敗。|否|  
    |`tlbid`|包含類別類型資訊的類型程式庫識別項。|否|  
  
     所有屬性標記都會區分大小寫。 您可以使用 OLE/COM ObjectViewer (Oleview.exe) 檢視針對組件所匯出的型別程式庫，以取得 CLSID、ProgID、執行緒模型和執行階段版本。  
  
     下列元件資訊清單識別兩個類別：`testClass1` 和 `testClass2`。  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"   
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5.  儲存並命名資訊清單檔。 元件資訊清單的名稱就是後接 .manifest 副檔名的組件庫名稱。 例如，myManagedComp.dll 是 myManagedComp.manifest。  
  
 您必須將元件資訊清單內嵌為組件中的資源。  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a>將元件資訊清單內嵌至 Managed 組件  
  
1.  建立包含下列陳述式的資源指令碼：  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     在此陳述式中，`myManagedComp.manifest` 是所內嵌之元件資訊清單的名稱。 在此範例中，指令碼檔名稱是 `myresource.rc`。  
  
2.  使用 Microsoft Windows 資源編譯器 (Rc.exe) 編譯指令碼。 在命令提示字元中輸入下列命令：  
  
     `rc myresource.rc`  
  
     Rc.exe 會產生 `myresource.res` 資源檔。  
  
3.  重新編譯組件的原始程式檔，然後使用 **/win32res** 選項來指定資源檔：  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     同樣地，`myresource.res` 是包含內嵌資源之資源檔的名稱。  
  
## <a name="see-also"></a>另請參閱
- [免註冊的 COM Interop](registration-free-com-interop.md)
- [免註冊 COM Interop 的需求](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))
- [設定適用於免註冊啟用的 COM 元件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))
- [免註冊啟用 .NET 架構元件：逐步解說](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))
