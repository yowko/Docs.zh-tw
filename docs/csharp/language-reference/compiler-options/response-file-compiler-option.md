---
title: '@ (C# 編譯器選項)'
ms.date: 07/20/2015
f1_keywords:
- '@'
helpviewer_keywords:
- response files, specifying for compilation [C#]
- '@ compiler option'
ms.assetid: dda4fa9f-a02c-400f-8b6a-d58834e13d7f
ms.openlocfilehash: facf2d45aff424d54dde45973cfec8cc8f93cb6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215065"
---
# <a name="-c-compiler-options"></a>@ (C# 編譯器選項)
@ 選項可讓您指定檔案，內含要編譯的編譯器選項和原始程式碼檔。  
  
## <a name="syntax"></a>語法  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>引數  
 `response_file`  
 列出要編譯之編譯器選項或原始程式碼檔的檔案。  
  
## <a name="remarks"></a>備註  
 編譯器將會處理編譯器選項和原始程式碼檔，就像已在命令列上指定它們一樣。  
  
 若要在編譯中指定多個回應檔，請指定多個回應檔選項。 例如:   
  
```  
@file1.rsp @file2.rsp  
```  
  
 在回應檔中，多個編譯器選項和原始程式碼檔可以出現在一行上。 單一編譯器選項規格必須出現在一行上 (無法跨越多行)。 回應檔可以有開頭為 # 符號的註解。  
  
 在回應檔內指定編譯器選項，就像在命令列上發出這些命令一樣。 如需詳細資訊，請參閱[從命令列建置](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。  
  
 編譯器會處理遇到的命令選項。 因此，命令列引數可以覆寫回應檔中先前列出的選項。 相反地，回應檔中的選項將會覆寫在命令列或其他回應檔中先前所列的選項。  
  
 C# 提供 csc.rsp 檔案，而此檔案位於與 csc.exe 檔案相同的目錄中。 如需 csc.rsp 的詳細資訊，請參閱 [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)。  
  
 無法在 Visual Studio 開發環境中設定此編譯器選項，也無法以程式設計方式進行變更。  
  
## <a name="example"></a>範例  
 以下是範例回應檔中的數行：  
  
```console  
# build the first output file  
-target:exe -out:MyExe.exe source1.cs source2.cs  
```  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
