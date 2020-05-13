---
title: 如何：在可當地語系化的應用程式中使用資源
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 8f516a86036656b98add23d38c588b5c19be4d7a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212471"
---
# <a name="how-to-use-resources-in-localizable-apps"></a>如何：在可當地語系化的應用程式中使用資源

當地語系化是指將使用者介面調整成不同的文化特性。 若要這樣做，您必須翻譯標題、標題和清單方塊專案等文字。 為了讓翻譯變得更容易，要轉譯的專案會收集到資源檔中。 如需如何建立資源檔以進行當地語系化的詳細資訊，請參閱[當地語系化應用程式](how-to-localize-an-application.md)。 若要讓 WPF 應用程式當地語系化，開發人員需要將所有可當地語系化的資源建立到資源元件中。 資源元件已當地語系化成不同的語言，而程式碼後置使用資源管理 API 來載入。

## <a name="example"></a>範例

WPF 應用程式所需的其中一個檔案是專案檔（proj）。 專案檔案應該包含您在應用程式中使用的所有資源。 下列 XAML 範例顯示這種情況。

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

若要在您的應用程式中使用資源，請具現化 <xref:System.Resources.ResourceManager> 並載入您要使用的資源。 下列 c # 程式碼示範如何執行這項操作。

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a>請參閱

- [將應用程式當地語系化](how-to-localize-an-application.md)
