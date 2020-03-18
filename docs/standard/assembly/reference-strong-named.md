---
title: 如何：引用強命名程式集
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156474"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>如何：引用強命名程式集
參考強式名稱組件中類型或資源的程序通常十分簡單。 您可以在編譯時間 (早期繫結) 或執行階段進行參考。  
  
當您向編譯器指示要編譯的程式集顯式引用另一個程式集時，將發生編譯時間引用。 當您使用編譯時間參考時，編譯器會自動取得目標強式名稱組件的公開金鑰，並將它放在所編譯組件的組件參考中。
  
> [!NOTE]
> 強式名稱的組件只可使用來自其他強式名稱組件的類型。 否則，強式名稱組件的安全性將會受到危害。  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>對強命名程式集進行編譯時引用  

在命令提示字元中，輸入下列命令：  

\<*編譯器命令*> **/引用：**\<*程式集名稱*>  

在這個命令中，「編譯器命令」** 是您所使用語言的編譯器命令，而「組件名稱」** 是所參考的強式名稱組件的名稱。 您也可以使用其他編譯器選項，例如 **/t:library** 選項來建立程式庫組件。  

下面的示例創建一個稱為*myAssembly.dll*的程式集，該程式集引用名為*myLibAssembly.dll*的強式名稱程式集，該程式集來自稱為*myAssembly.cs*的代碼模組。  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>對強命名程式集進行運行時引用  
  
在運行時引用強命名程式集時（例如通過使用<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>or<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>方法）時，必須使用引用的強命名程式集的顯示名稱。 顯示名稱的語法如下：  

\<*程式集名稱*>**、**\<*版本號*>**、** \<*區域性*>**、** \<*公開金鑰權杖*>  

例如：  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

在此範例中，`PublicKeyToken` 是公開金鑰權杖的十六進位格式。 如果沒有文化特性值，請使用 `Culture=neutral`。  

下列程式碼範例示範如何搭配使用這項資訊與 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

您可以使用下列[強式名稱 (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) 命令，列印特定組件之公開金鑰和公開金鑰權杖的十六進位格式：  

**sn -Tp \< ** *程式集***>**  

如果您有公開金鑰檔案，則可以改用下列命令 (請注意命令列選項上的大小寫差異)：  

**sn -tp \<** *公開金鑰檔* **>**  

## <a name="see-also"></a>另請參閱

- [建立和使用強式名稱的組件](create-use-strong-named.md)
