---
title: "-nostdlib (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nostdlib
dev_langs:
- CSharp
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1d500e2e55ab3117aa674e11d6cdd25703035879
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="nostdlib-c-compiler-options"></a>/nostdlib (C# 編譯器選項)
**/nostdlib** 會導致無法匯入 mscorlib.dll，它定義了整個系統命名空間。  
  
## <a name="syntax"></a>語法  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>備註  
 如果您想要定義或建立自己的系統命名空間和物件，請使用此選項。  
  
 如果您未指定 **/nostdlib**，mscorlib.dll 會匯入到您的程式 (與指定 **/nostdlib-**相容)。 指定 **/nostdlib** 等同於指定 **/nostdlib+**。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性]  頁面。  
  
2.  按一下 [建置]  屬性頁面。  
  
3.  按一下 [ **進階** ] 按鈕。  
  
4.  修改 [不要參考 mscorlib.dll]  屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)

