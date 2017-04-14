---
title: "如何：設定免註冊啟用的 .NET Framework 架構 COM 元件 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "啟動, 免註冊"
  - "應用程式資訊清單 [.NET Framework]"
  - "元件 [.NET Framework], 資訊清單"
  - "資訊清單 [.NET Framework]"
  - "免註冊的 COM Interop, 設定 .NET 架構元件"
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：設定免註冊啟用的 .NET Framework 架構 COM 元件
.NET Framework 元件的免註冊啟動只比 COM 元件的免註冊啟動稍微複雜一些。  此設定需要兩種資訊清單：  
  
-   COM 應用程式必須擁有 Win32 樣式應用程式資訊清單來辨識 Managed 元件  
  
-   .NET Framework 元件必須擁有在執行階段時所需之啟動資訊的元件資訊清單  
  
 這個主題說明如何將應用程式資訊清單與應用程式關聯在一起；並在組件中嵌入元件資訊清單。  
  
### 若要建立應用程式資訊清單  
  
1.  使用 XML 編輯器，建立 \(或修改\) COM 應用程式所擁有的應用程式資訊清單，來與一個或多個 Managed 元件互通。  
  
2.  在檔案開頭插入下列標準標頭：  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
     如需資訊清單項目和其屬性的詳細資訊，請在 MSDN Library 中搜尋 "Application Manifests Reference"。  
  
3.  識別資訊清單的擁有人。  在下列範例中，`myComApp` 1 版擁有資訊清單檔。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"   
                        name="myOrganization.myDivision.myComApp"   
                        version="1.0.0.0"   
                        processorArchitecture="msil"   
      />  
    ```  
  
4.  識別相依組件。  在下列範例中，`myComApp` 依存在 `myManagedComp` 上。  
  
    ```  
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
  
5.  儲存和命名資訊清單檔。  應用程式資訊清單的名稱為組件可執行檔的名稱再加上 .manifest 副檔名於其後。  例如，myComApp.exe 的應用程式資訊清單檔名稱為 myComApp.exe.manifest。  
  
 您可以在與 COM 應用程式相同的目錄之下，安裝應用程式資訊清單。  要不然，您可以將它當做資源加入應用程式的 .exe 檔中。  如需詳細資訊，請在 MSDN Library 中搜尋 "Side\-by\-side Assemblies"。  
  
#### 若要建立元件資訊清單  
  
1.  使用 XML 編輯器，建立元件資訊清單來描述 Managed 組件。  
  
2.  在檔案開頭插入下列標準標頭：  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
    ```  
  
3.  識別檔案的擁有人。  在應用程式資訊清單檔中，`<dependentAssembly>` 項目的 `<assemblyIdentity>` 項目，必須與元件資訊清單中的項目相符。  在下列範例中，`myManagedComp` 1.2.3.4 版擁有資訊清單檔。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />  
    ```  
  
4.  識別組件中的每一個類別。  在 Managed 組件中，使用 `<clrClass>` 項目來唯一識別每一個類別。  此項目是 `<assembly>` 項目的子項目，下表說明其所擁有的屬性。  
  
    |屬性|描述|必要項|  
    |--------|--------|---------|  
    |`clsid`|指定啟動類別的識別項。|是|  
    |`description`|告知使用者關於元件資訊的字串。  預設為空字串。|否|  
    |`name`|表示 Managed 類別的字串。|是|  
    |`progid`|用於晚期繫結啟動的識別項。|否|  
    |`threadingModel`|COM 執行緒模型。"Both" 為預設值。|否|  
    |`runtimeVersion`|指定要使用的 Common Language Runtime \(CLR\) 版本。  如果您未指定此屬性，且 CLR 尚未載入，會以 CLR 第 4 版之前的最新安裝 CLR 載入元件。  如果您指定 v1.0.3705、v1.1.4322 或 v2.0.50727，版本會自動回復為 CLR 第 4 版之前的最新安裝 CLR \(通常為 v2.0.50727\)。  如果已載入其他版本的 CLR，而指定的版本可以在同處理序並存載入，則會載入指定的版本；否則，會使用已載入的 CLR。  這可能會導致載入失敗。|否|  
    |`tlbid`|包含關於類別型別資訊的型別程式庫識別項。|否|  
  
     所有的屬性標籤都區分大小寫。  藉由使用 OLE\/COM ObjectViewer \(Oleview.exe\) 來檢視匯出的型別程式庫組件，您可以獲得 CLSID、ProgID、執行緒模型和執行階段版本。  
  
     下列元件資訊清單辨識單兩個類別：`testClass1` 與 `testClass2`。  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4" />  
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
  
5.  儲存和命名資訊清單檔。  元件資訊清單的名稱為組件程式庫的名稱，後面再加上 .manifest 副檔名。  例如，myManagedComp.dll 的元件資訊清單名稱為 myManagedComp.manifest。  
  
 您必須將元件資訊清單當做資源嵌入組件中。  
  
#### 若要嵌入元件資訊清單至 Managed 組件中  
  
1.  建立包含下列陳述式的資源指令碼 \(Script\)：  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     在此陳述式中，`myManagedComp.manifest` 是嵌入的元件資訊清單名稱。  這個範例的指令碼檔案名稱為 `myresource.rc`。  
  
2.  使用 Microsoft Windows Resource Compiler \(Rc.exe\) 來編譯該指令碼。  在命令提示字元中輸入下列命令：  
  
     `rc myresource.rc`  
  
     Rc.exe 產生 `myresource.res` 資源檔。  
  
3.  再次編譯組件的資源檔，並使用 **\/win32res** 選項指定資源檔：  
  
    ```  
    /win32res:myresource.res  
    ```  
  
     `myresource.res` 會再一次成為含有內嵌資源之資源檔的名稱。  
  
## 請參閱  
 [免註冊的 COM Interop](../../../docs/framework/interop/registration-free-com-interop.md)   
 [Requirements for Registration\-Free COM Interop](http://msdn.microsoft.com/zh-tw/0c43bc57-eecf-4e6c-8114-490141cce4da)   
 [Configuring COM Components for Registration\-Free Activation](http://msdn.microsoft.com/zh-tw/bfe9b02f-d964-4784-960e-a1f94692fbfe)   
 [.NET 架構元件之免註冊啟動: A Walkthrough](http://go.microsoft.com/fwlink/?LinkId=158812)