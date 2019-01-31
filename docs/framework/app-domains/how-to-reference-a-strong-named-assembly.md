---
title: HOW TO：參考以強式名稱命名的組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 520bce0dbc9f3e9ade9d9fbcb1529a5433b0d87c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596068"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>HOW TO：參考以強式名稱命名的組件
參考強式名稱組件中類型或資源的程序通常十分簡單。 您可以在編譯時間 (早期繫結) 或執行階段進行參考。  
  
 當您對編譯器指出您的組件明確參考另一個組件時，就會發生編譯時間參考。 當您使用編譯時間參考時，編譯器會自動取得目標強式名稱組件的公開金鑰，並將它放在所編譯組件的組件參考中。  
  
> [!NOTE]
>  強式名稱的組件只可使用來自其他強式名稱組件的類型。 否則，強式名稱組件的安全性將會受到危害。  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>建立強式名稱組件的編譯時間參考  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<*編譯器命令*> **/reference:**\<組件名稱>  
  
     在這個命令中，「編譯器命令」是您所使用語言的編譯器命令，而「組件名稱」是所參考的強式名稱組件的名稱。 您也可以使用其他編譯器選項，例如 **/t:library** 選項來建立程式庫組件。  
  
 下列範例會建立稱為 `myAssembly.dll` 的組件，而此組件從稱為 `myAssembly.cs` 的程式碼模組參考稱為 `myLibAssembly.dll` 的強式名稱組件。  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>建立強式名稱組件的執行階段參考  
  
1.  當您建立強式名稱組件的執行階段參考時 (例如，使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 或 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> 方法)，必須使用所參考之強式名稱組件的顯示名稱。 顯示名稱的語法如下：  
  
     \<組件名稱>**,** \<版本號碼>**,** \<文化特性>**,** \<公開金鑰權杖>  
  
     例如：  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     在此範例中，`PublicKeyToken` 是公開金鑰權杖的十六進位格式。 如果沒有文化特性值，請使用 `Culture=neutral`。  
  
 下列程式碼範例示範如何搭配使用這項資訊與 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 您可以使用下列[強式名稱 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 命令，列印特定組件之公開金鑰和公開金鑰權杖的十六進位格式：  
  
 **sn-Tp \<**  *組件* **>**  
  
 如果您有公開金鑰檔案，則可以改用下列命令 (請注意命令列選項上的大小寫差異)：  
  
 **sn -tp \<** *公開金鑰檔* **>**  
  
## <a name="see-also"></a>另請參閱
- [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
