---
title: "-subsystemversion （C# 編譯器選項） | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# /subsystemversion (C# 編譯器選項)
指定的子系統可以執行產生的可執行檔，以決定可以執行的可執行檔的 Windows 版本的最小版本。 大多數情況下，此選項可確保可執行檔可以利用特定的安全性功能，與舊版本的 Windows。  
  
> [!NOTE]
>  若要指定的子系統本身，請使用 [/目標](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 編譯器選項。  
  
## <a name="syntax"></a>語法  
  
```  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>參數  
 `major.minor`  
 最小必要版本的子系統，主要和次要版本的點標記法中表示。 例如，您可以指定應用程式不能是早於 Windows 7 如果您將此選項的值設定為 6.01，如本主題稍後的表格所述的作業系統上執行。 您必須指定的值 `major` 和 `minor` 為整數。  
  
 前置歸零，然後 `minor` 版本不會變更版本，但尾端為零。 比方說，6.1 和 6.01 參考相同的版本，但 6.10 指的是不同的版本。 我們建議以避免產生混淆的兩位數表示的次要版本。  
  
## <a name="remarks"></a>備註  
 下表列出常見的子系統版本的 Windows。  
  
|Windows 版本|子系統的版本|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>預設值  
 預設值的 **/subsystemversion** 編譯器選項取決於下列清單中的條件︰  
  
-   預設值為 6.02，如果下列清單中的任何編譯器選項設定︰  
  
    -   [/target: appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [/target: winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [/platform:arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   如果您使用 MSBuild，預設值是 6.00、 您的目標 [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net-v45-md.md)], ，而且您還沒有設定任何稍早在此清單中所指定的編譯器選項。  
  
-   預設值是 4.00 如果前一個條件為 true。  
  
## <a name="setting-this-option"></a>設定這個選項  
 若要設定 **/subsystemversion** 編譯器選項在 Visual Studio 中，您必須開啟.csproj 檔，並指定的值 `SubsystemVersion` MSBuild XML 中的屬性。 您無法在 Visual Studio IDE 中設定這個選項。 詳細資訊，請參閱本主題前面的 「 預設值 」 或 [一般 MSBuild 專案屬性](/visual-studio/msbuild/common-msbuild-project-properties)。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)