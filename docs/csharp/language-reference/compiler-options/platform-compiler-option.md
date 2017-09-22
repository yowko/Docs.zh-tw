---
title: "-platform (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /platform
dev_langs:
- CSharp
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 44d4cadbc45eb141ecb7a83345d2a7a834ce5299
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="platform-c-compiler-options"></a>/platform (C# 編譯器選項)
指定哪個 Common Language Runtime (CLR) 版本可以執行組件。  
  
## <a name="syntax"></a>語法  
  
```console  
/platform:string  
```  
  
#### <a name="parameters"></a>參數  
 `string`  
 anycpu (預設值)、anycpu32bitpreferred、ARM、x64、x86 或 Itanium。  
  
## <a name="remarks"></a>備註  
  
-   **anycpu** (預設值) 會將組件編譯為可在所有平台上執行。 您的應用程式會盡可能做為 64 位元處理序執行，而且只有在 32 位元模式可用時才會回到該模式。  
  
-   **anycpu32bitpreferred** 會將組件編譯為可在所有平台上執行。 您的應用程式在同時支援 64 位元和 32 位元應用程式的系統上會以 32 位元模式執行。 您只能針對以 .NET Framework 4.5 為目標的專案指定此選項。  
  
-   **ARM** 會將您的組件編譯為可在採用 Advanced RISC Machine (ARM) 處理器的電腦上執行。  
  
-   **x64** 會在支援 AMD64 或 EM64T 指令集的電腦上編譯將由 64 位元 Common Language Runtime 所執行的組件。  
  
-   **x86** 會編譯將由 32 位元、x86 相容的 Common Language Runtime 所執行的組件。  
  
-   **Itanium** 會在使用 Itanium 處理器的電腦上編譯將由 64 位元 Common Language Runtime 所執行的組件。  
  
 在 64 位元 Windows 作業系統上：  
  
-   使用 **/platform:x86** 所編譯的組件會在 WOW64 下執行的 32 位元 CLR 上執行。  
  
-   使用 **/platform:anycpu** 所編譯的 DLL 會在與載入它的程序相同的 CLR 上執行。  
  
-   使用 **/platform:anycpu** 所編譯的可執行檔會在 64 位元 CLR 上執行。  
  
-   使用 **/platform:anycpu32bitpreferred** 所編譯的可執行檔會在 32 位元 CLR 上執行。  
  
 **anycpu32bitpreferred** 設定只對可執行檔 (.EXE) 有效，而且需要 .NET Framework 4.5。  
  
 如需開發要在 Windows 64 位元作業系統上執行之應用程式的詳細資訊，請參閱 [64 位元應用程式](https://msdn.microsoft.com/library/ms241064)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性]  頁面。  
  
2.  按一下 [建置] 屬性頁面。  
  
3.  修改**平台目標**屬性，並且針對以 .NET Framework 4.5 為目標的專案選取或清除 [建議使用 32 位元] 核取方塊。  
  
 請注意，在 Visual C# Express 開發環境中無法使用 **/platform**。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 **/platform** 選項，指定應用程式應該在 64 位元 Windows 作業系統上以 64 位元 CLR 執行。  
  
```console  
csc /platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](index.md)   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)

