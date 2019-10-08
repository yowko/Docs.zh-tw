---
title: HOW TO：讓實體可序列化
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002706"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="d68ae-102">HOW TO：讓實體可序列化</span><span class="sxs-lookup"><span data-stu-id="d68ae-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="d68ae-103">在產生程式碼時，您可以讓實體成為可序列化。</span><span class="sxs-lookup"><span data-stu-id="d68ae-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="d68ae-104">實體類別會使用 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性予以裝飾，而資料行則使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性予以裝飾。</span><span class="sxs-lookup"><span data-stu-id="d68ae-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="d68ae-105">使用 Visual Studio 的開發人員可以使用物件關聯式設計工具來實現此目的。</span><span class="sxs-lookup"><span data-stu-id="d68ae-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="d68ae-106">如果您使用 SQLMetal 命令列工具，請使用 **/serialization**選項搭配 `unidirectional` 引數。</span><span class="sxs-lookup"><span data-stu-id="d68ae-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="d68ae-107">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="d68ae-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d68ae-108">範例</span><span class="sxs-lookup"><span data-stu-id="d68ae-108">Example</span></span>  
 <span data-ttu-id="d68ae-109">下列 SQLMetal 命令列會產生具有可序列化實體的檔案。</span><span class="sxs-lookup"><span data-stu-id="d68ae-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="d68ae-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d68ae-110">See also</span></span>

- [<span data-ttu-id="d68ae-111">序列化</span><span class="sxs-lookup"><span data-stu-id="d68ae-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="d68ae-112">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="d68ae-112">Creating the Object Model</span></span>](creating-the-object-model.md)
