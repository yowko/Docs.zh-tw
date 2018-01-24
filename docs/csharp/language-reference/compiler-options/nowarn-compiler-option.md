---
title: "-nowarn (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2784e63b7c1e67b32fc448b4b112ad0252b1abd9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# 編譯器選項)
**-nowarn** 選項可讓您隱藏編譯器不顯示一或多個警告。 請以逗點分隔多個警告編號。  
  
## <a name="syntax"></a>語法  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>引數  
 `number1`, `number2`  
 您想要編譯器隱藏的警告編號。  
  
## <a name="remarks"></a>備註  
 您應該只要指定警告識別項的數值部分。 例如，如果您想要隱藏 CS0028，您可以指定 `-nowarn:28`。  
  
 編譯器會以無訊息方式略過傳遞給 `-nowarn` 的警告編號，它在舊版中有效但已自編譯器移除。 例如，CS0679 在 Visual Studio .NET 2002 的編譯器中有效，但後來已移除。  
  
 `-nowarn` 選項無法隱藏下列警告︰  
  
-   編譯器警告 (層級 1) CS2002  
  
-   編譯器警告 (層級 1) CS2023  
  
-   編譯器警告 (層級 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性]  頁面。 如需詳細資料，請參閱[專案設計工具、建置頁 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。  
  
2.  按一下 [建置] 屬性頁面。  
  
3.  修改**隱藏警告**屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)  
 [C# 編譯器錯誤](../../../csharp/language-reference/compiler-messages/index.md)
