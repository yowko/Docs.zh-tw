---
title: "HOW TO：在 .NET Framework 4 下執行的 IIS 中，裝載以 .NET Framework 3.5 寫入的 WCF 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9aabc785-068d-4d32-8841-3ef39308d8d6
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# HOW TO：在 .NET Framework 4 下執行的 IIS 中，裝載以 .NET Framework 3.5 寫入的 WCF 服務
在執行 [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] 的電腦上裝載以 [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] 撰寫的 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務時，可能會收到包含下列文字的 <xref:System.ServiceModel.ProtocolException>。  
  
```Output  
未處理的例外狀況: System.ServiceModel.ProtocolException: 回應訊息的內容類型文字/html; 字元集=utf-8 與繫結 (應用程式/soap+xml; 字元集=utf-8) 的內容類型不符。如果使用自訂編碼器，請確定已正確實作 IsContentTypeSupported 方法。回應的前 1024 個位元為: '<html>    <head>        <title> 應用程式網域或應用程式集區目前執行的版本為 .NET Framework 4 或更新版本。如果此 Web 應用程式的 IIS 設定已設為 4.0 或更新版本，或您正在使用 ASP.NET Web 程式開發伺服器 4.0 或更新版本，就會發生此問題。此 Web 應用程式之 Web.config 檔案中的 <compilation> 項目未包含此 .NET Framework 版本所需的必要 'targetFrameworkMoniker' 屬性 (例如，'<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">')。請使用此屬性更新 Web.config 檔案，或設定 Web 應用程式使用其他版本的 .NET Framework。</title>...  
```  
  
 或者，如果您嘗試瀏覽至服務的 .svc 檔，則可能會看到包含下列文字的錯誤網頁。  
  
```Output  
應用程式網域或應用程式集區目前執行的版本為 .NET Framework 4.0 (含) 以後版本。如果此 Web 應用程式的 IIS 設定已設為 4.0 或更新版本，或您正在使用 ASP.NET Web 程式開發伺服器 4.0 或更新版本，就會發生此問題。此 Web 應用程式之 Web.config 檔案中的 <compilation> 項目未包含此 .NET Framework 版本所需的必要 'targetFrameworkMoniker' 屬性 ('<compilation targetFrameworkMoniker=".NETFramework,Version=v4.0">')。請使用此屬性更新 Web.config 檔案，或設定 Web 應用程式使用其他版本的 .NET Framework。  
```  
  
 因為應用程式網域 IIS 執行的是 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]，而 WCF 服務預期在 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 下執行，所以會發生這些錯誤。本主題說明要讓服務執行所需進行的修改。  
  
 接著，尋找 \<`compilers`\> 項目，並且將 CompilerVersion 提供者選項的值變更為 4.0。根據預設，\<`compilers`\> 項目底下會有兩個 \<`compiler`\> 項目。您必須更新這兩個項目的 CompilerVersion 提供者選項，如下列範例所示。  
  
```  
<system.codedom>  
      <compilers>  
        <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                  type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
        <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                  type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
          <providerOption name="CompilerVersion" value="v3.5"/>  
          <providerOption name="OptionInfer" value="true"/>  
          <providerOption name="WarnAsError" value="false"/>  
        </compiler>  
      </compilers>  
    </system.codedom>  
```  
  
### 加入必要的 targetFramework 屬性  
  
1.  開啟服務的 Web.config 檔案並尋找 \<`compilation`\> 項目。  
  
2.  將 `targetFramework` 屬性加入至 \<`compilation`\> 項目，如下列範例所示。  
  
    ```  
    <compilation debug="false"  
            targetFramework="4.0">  
  
            <assemblies>  
              <add assembly="System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Xml.Linq, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
              <add assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>  
              <add assembly="System.Data.DataSetExtensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
            </assemblies>  
  
          </compilation>  
    ```  
  
3.  尋找 \<`compilers`\> 項目，並且將 CompilerVersion 提供者選項的值變更為 4.0。根據預設，\<`compilers`\> 項目底下會有兩個 \<`compiler`\> 項目。您必須更新這兩個項目的 CompilerVersion 提供者選項，如下列範例所示。  
  
    ```  
    <system.codedom>  
          <compilers>  
            <compiler language="c#;cs;csharp" extension=".cs" warningLevel="4"  
                      type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
            <compiler language="vb;vbs;visualbasic;vbscript" extension=".vb" warningLevel="4"  
                      type="Microsoft.VisualBasic.VBCodeProvider, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
              <providerOption name="CompilerVersion" value="v3.5"/>  
              <providerOption name="OptionInfer" value="true"/>  
              <providerOption name="WarnAsError" value="false"/>  
            </compiler>  
          </compilers>  
        </system.codedom>  
    ```