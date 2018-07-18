---
title: 'Abfragen und Suchen von Entitäten: EF6'
author: divega
ms.date: 2016-10-23
ms.prod: entity-framework
ms.author: divega
ms.manager: avickers
ms.technology: entity-framework-6
ms.topic: article
ms.assetid: 65bb3db2-2226-44af-8864-caa575cf1b46
caps.latest.revision: 3
ms.openlocfilehash: 92467e1a93f576eca627cf7b7d2351054a882c2c
ms.sourcegitcommit: 00cb52625b57c1ea339ded1454179fe89b6bcfea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2018
ms.locfileid: "39067546"
---
# <a name="querying-and-finding-entities"></a><span data-ttu-id="7dffd-102">Abfragen und Suchen von Entitäten</span><span class="sxs-lookup"><span data-stu-id="7dffd-102">Querying and Finding Entities</span></span>
<span data-ttu-id="7dffd-103">Dieses Thema behandelt die verschiedenen Methoden, mit denen Sie Daten über Entity Framework abfragen können, einschließlich LINQ und der Find-Methode.</span><span class="sxs-lookup"><span data-stu-id="7dffd-103">This topic covers the various ways you can query for data using Entity Framework, including LINQ and the Find method.</span></span> <span data-ttu-id="7dffd-104">Die in diesem Thema dargestellten Techniken gelten jeweils für Modelle, die mit Code First und dem EF-Designer erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="7dffd-104">The techniques shown in this topic apply equally to models created with Code First and the EF Designer.</span></span>  

## <a name="finding-entities-using-a-query"></a><span data-ttu-id="7dffd-105">Suchen von Entitäten über eine Abfrage</span><span class="sxs-lookup"><span data-stu-id="7dffd-105">Finding entities using a query</span></span>  

<span data-ttu-id="7dffd-106">DbSet und IDbSet implementieren IQueryable, was als Startpunkt zum Schreiben einer LINQ-Abfrage für die Datenbank verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="7dffd-106">DbSet and IDbSet implement IQueryable and so can be used as the starting point for writing a LINQ query against the database.</span></span> <span data-ttu-id="7dffd-107">In diesem Artikel wird LINQ nicht ausführlich erläutert, jedoch finden Sie nachstehend einige einfache Beispiele:</span><span class="sxs-lookup"><span data-stu-id="7dffd-107">This is not the appropriate place for an in-depth discussion of LINQ, but here are a couple of simple examples:</span></span>  

``` csharp
using (var context = new BloggingContext())
{
    // Query for all blogs with names starting with B
    var blogs = from b in context.Blogs
                   where b.Name.StartsWith("B")
                   select b;

    // Query for the Blog named ADO.NET Blog
    var blog = context.Blogs
                    .Where(b => b.Name == "ADO.NET Blog")
                    .FirstOrDefault();
}
```  

<span data-ttu-id="7dffd-108">Beachten Sie, dass DbSet und IDbSet immer Abfragen für die Datenbank erstellen und immer einen Roundtrip zur Datenbank mit sich bringen, auch wenn die zurückgegebenen Entitäten bereits im Kontext vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="7dffd-108">Note that DbSet and IDbSet always create queries against the database and will always involve a round trip to the database even if the entities returned already exist in the context.</span></span> <span data-ttu-id="7dffd-109">Eine Abfrage wird für die Datenbank ausgeführt, wenn:</span><span class="sxs-lookup"><span data-stu-id="7dffd-109">A query is executed against the database when:</span></span>  

- <span data-ttu-id="7dffd-110">Sie durch eine **foreach**-Anweisung (C#) oder eine **ForEach**-Anweisung (Visual Basic) aufgezählt wird.</span><span class="sxs-lookup"><span data-stu-id="7dffd-110">It is enumerated by a **foreach** (C#) or **For Each** (Visual Basic) statement.</span></span>  
- <span data-ttu-id="7dffd-111">Sie wird von einem Auflistungsvorgang wie [ToArray](https://msdn.microsoft.com/library/bb298736), [ToDictionary](https://msdn.microsoft.com/library/system.linq.enumerable.todictionary) oder [ToList](https://msdn.microsoft.com/library/bb342261) aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="7dffd-111">It is enumerated by a collection operation such as [ToArray](https://msdn.microsoft.com/library/bb298736), [ToDictionary](https://msdn.microsoft.com/library/system.linq.enumerable.todictionary), or [ToList](https://msdn.microsoft.com/library/bb342261).</span></span>  
- <span data-ttu-id="7dffd-112">LINQ-Operatoren, wie beispielsweise [First](https://msdn.microsoft.com/library/bb291976) oder [Any](https://msdn.microsoft.com/library/bb337697), werden im äußersten Teil der Abfrage angegeben.</span><span class="sxs-lookup"><span data-stu-id="7dffd-112">LINQ operators such as [First](https://msdn.microsoft.com/library/bb291976) or [Any](https://msdn.microsoft.com/library/bb337697) are specified in the outermost part of the query.</span></span>  
- <span data-ttu-id="7dffd-113">Die folgenden Methoden werden aufgerufen: die Erweiterungsmethode [Load](https://msdn.microsoft.com/library/system.data.entity.dbextensions.load) (auf einem DBSet), [DbEntityEntry.Reload](https://msdn.microsoft.com/library/system.data.entity.infrastructure.dbentityentry.reload.aspx) und Database.ExecuteSqlCommand.</span><span class="sxs-lookup"><span data-stu-id="7dffd-113">The following methods are called: the [Load](https://msdn.microsoft.com/library/system.data.entity.dbextensions.load) extension method on a DbSet, [DbEntityEntry.Reload](https://msdn.microsoft.com/library/system.data.entity.infrastructure.dbentityentry.reload.aspx), and Database.ExecuteSqlCommand.</span></span>  

<span data-ttu-id="7dffd-114">Wenn Ergebnisse von der Datenbank zurückgegeben werden, werden Objekte, die nicht im Kontext vorhanden sind, an den Kontext angefügt.</span><span class="sxs-lookup"><span data-stu-id="7dffd-114">When results are returned from the database, objects that do not exist in the context are attached to the context.</span></span> <span data-ttu-id="7dffd-115">Wenn sich ein Objekt bereits im Kontext befindet, wird das vorhandene Objekt zurückgegeben (die aktuellen und ursprünglichen Werte der Objekteigenschaften im Eintrag werden **nicht** mit Datenquellenwerten überschrieben).</span><span class="sxs-lookup"><span data-stu-id="7dffd-115">If an object is already in the context, the existing object is returned (the current and original values of the object's properties in the entry are **not** overwritten with database values).</span></span>  

<span data-ttu-id="7dffd-116">Wenn Sie eine Abfrage ausführen, werden Entitäten, die zum Kontext hinzugefügt wurden, jedoch nicht auf der Datenbank gespeichert wurden, nicht als Teil des Resultsets zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7dffd-116">When you perform a query, entities that have been added to the context but have not yet been saved to the database are not returned as part of the result set.</span></span> <span data-ttu-id="7dffd-117">Unter [Entity Framework Local Data (Lokale Daten von Entity Framework)](~/ef6/querying/local-data.md) erhalten Sie Informationen zum Abrufen von Daten, die sich im Kontext befinden.</span><span class="sxs-lookup"><span data-stu-id="7dffd-117">To get the data that is in the context, see [Local Data](~/ef6/querying/local-data.md).</span></span>  

<span data-ttu-id="7dffd-118">Wenn eine Abfrage keine Zeilen aus der Datenbank zurückgibt, ist das Ergebnis eine leere Sammlung anstatt **NULL**.</span><span class="sxs-lookup"><span data-stu-id="7dffd-118">If a query returns no rows from the database, the result will be an empty collection, rather than **null**.</span></span>  

## <a name="finding-entities-using-primary-keys"></a><span data-ttu-id="7dffd-119">Suchen von Entitäten über Primärschlüssel</span><span class="sxs-lookup"><span data-stu-id="7dffd-119">Finding entities using primary keys</span></span>  

<span data-ttu-id="7dffd-120">Die Find-Methoden auf DbSet verwendet den Primärschlüsselwert, um eine Entität, die vom Kontext nachverfolgt wird, zu finden.</span><span class="sxs-lookup"><span data-stu-id="7dffd-120">The Find method on DbSet uses the primary key value to attempt to find an entity tracked by the context.</span></span> <span data-ttu-id="7dffd-121">Wenn die Entität im Kontext nicht gefunden wird, wird eine Abfrage an die Datenbank gesendet, um dort die Entität zu suchen.</span><span class="sxs-lookup"><span data-stu-id="7dffd-121">If the entity is not found in the context then a query will be sent to the database to find the entity there.</span></span> <span data-ttu-id="7dffd-122">Wenn die Entität nicht im Kontext oder in der Datenbank gefunden wird, wird NULL zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="7dffd-122">Null is returned if the entity is not found in the context or in the database.</span></span>  

<span data-ttu-id="7dffd-123">„Find“ unterscheidet sich von der Verwendung einer Abfrage in zwei Punkten:</span><span class="sxs-lookup"><span data-stu-id="7dffd-123">Find is different from using a query in two significant ways:</span></span>  

- <span data-ttu-id="7dffd-124">Es wird nur ein Roundtrip zur Datenbank durchgeführt, wenn die Entität im angegebenen Schlüssel nicht im Kontext gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="7dffd-124">A round-trip to the database will only be made if the entity with the given key is not found in the context.</span></span>  
- <span data-ttu-id="7dffd-125">„Find“ gibt Entitäten zurück, die den Zustand „Added“ (Hinzugefügt) aufweisen.</span><span class="sxs-lookup"><span data-stu-id="7dffd-125">Find will return entities that are in the Added state.</span></span> <span data-ttu-id="7dffd-126">Das bedeutet, dass „Find“ Entitäten zurückgibt, die zum Kontext hinzugefügt, jedoch noch nicht in der Datenbank gespeichert wurden.</span><span class="sxs-lookup"><span data-stu-id="7dffd-126">That is, Find will return entities that have been added to the context but have not yet been saved to the database.</span></span>  
### <a name="finding-an-entity-by-primary-key"></a><span data-ttu-id="7dffd-127">Suchen nach einer Entität nach Primärschlüsseln</span><span class="sxs-lookup"><span data-stu-id="7dffd-127">Finding an entity by primary key</span></span>  

<span data-ttu-id="7dffd-128">Der folgende Code zeigt einige Verwendungsmöglichkeiten für „Find“:</span><span class="sxs-lookup"><span data-stu-id="7dffd-128">The following code shows some uses of Find:</span></span>  

``` csharp
using (var context = new BloggingContext())
{
    // Will hit the database
    var blog = context.Blogs.Find(3);

    // Will return the same instance without hitting the database
    var blogAgain = context.Blogs.Find(3);

    context.Blogs.Add(new Blog { Id = -1 });

    // Will find the new blog even though it does not exist in the database
    var newBlog = context.Blogs.Find(-1);

    // Will find a User which has a string primary key
    var user = context.Users.Find("johndoe1987");
}
```  

### <a name="finding-an-entity-by-composite-primary-key"></a><span data-ttu-id="7dffd-129">Suchen nach einer Entität nach zusammengesetztem Primärschlüsseln (Verbundprimärschlüssel)</span><span class="sxs-lookup"><span data-stu-id="7dffd-129">Finding an entity by composite primary key</span></span>  

<span data-ttu-id="7dffd-130">Entity Framework lässt zusammengesetzte Schlüssel für Ihre Entität zu. Diese sind Schlüssel, die aus mehr aus einer Eigenschaft bestehen.</span><span class="sxs-lookup"><span data-stu-id="7dffd-130">Entity Framework allows your entities to have composite keys - that's a key that is made up of more than one property.</span></span> <span data-ttu-id="7dffd-131">Sie verfügen z.B. über die Entität „BlogSettings“, die eine Benutzereinstellung für einen bestimmten Blog darstellt.</span><span class="sxs-lookup"><span data-stu-id="7dffd-131">For example, you could have a BlogSettings entity that represents a users settings for a particular blog.</span></span> <span data-ttu-id="7dffd-132">Da ein Benutzer immer nur eine BlogSettings-Entität für jeden Blog besitzen würde, könnten Sie aus dem Primärschlüssel von BlogSettings eine Kombination aus BlogId und Benutzername machen.</span><span class="sxs-lookup"><span data-stu-id="7dffd-132">Because a user would only ever have one BlogSettings for each blog you could chose to make the primary key of BlogSettings a combination of BlogId and Username.</span></span> <span data-ttu-id="7dffd-133">Durch folgenden Code wird versucht, BlogSettings mit BlogId = 3 und Benutzername = „johndoe1987“ zu finden.</span><span class="sxs-lookup"><span data-stu-id="7dffd-133">The following code attempts to find the BlogSettings with BlogId = 3 and Username = "johndoe1987":</span></span>  

``` csharp  
using (var context = new BloggingContext())
{
    var settings = context.BlogSettings.Find(3, "johndoe1987");
}
```  

<span data-ttu-id="7dffd-134">Wenn Sie über zusammengesetzte Schlüssel verfügen, dann beachten Sie, dass Sie das ColumnAttribute oder die Fluent-API verwenden müssen, um eine Reihenfolge für die Eigenschaften der zusammengesetzten Schlüssel anzugeben.</span><span class="sxs-lookup"><span data-stu-id="7dffd-134">Note that when you have composite keys you need to use ColumnAttribute or the fluent API to specify an ordering for the properties of the composite key.</span></span> <span data-ttu-id="7dffd-135">Der Aufruf von „Find“ muss diese Reihenfolge verwenden, wenn die Werte, aus denen der Schlüssel besteht, angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="7dffd-135">The call to Find must use this order when specifying the values that form the key.</span></span>  