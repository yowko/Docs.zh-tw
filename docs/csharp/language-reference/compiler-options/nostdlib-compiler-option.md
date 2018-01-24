---
title: "-nostdlib (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dd9d2b6a4a9c774aa339e840ad0020ee39cb10d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# 編譯器選項)
**-nostdlib** 會導致無法匯入 mscorlib.dll，而此檔案定義整個系統命名空間。  
  
## <a name="syntax"></a>語法  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>備註  
 如果您想要定義或建立自己的系統命名空間和物件，請使用此選項。  
  
 如果您未指定 **-nostdlib**，則 mscorlib.dll 會匯入至您的程式 (與指定 **-nostdlib-** 相容)。 指定 **-nostdlib** 等同於指定 **-nostdlib+**。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性]  頁面。  
  
2.  按一下 [建置]  屬性頁面。  
  
3.  按一下 [ **進階** ] 按鈕。  
  
4.  修改 [不要參考 mscorlib.dll]  屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
