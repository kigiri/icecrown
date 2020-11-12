# icecrown
*interactive spawn map*
----

Data source:
  - [mamytwink.com](https://www.mamytwink.com/actualite/invasion-du-fleau-horaires-de-lapparition-des-boss-de-la-couronne-de-glace#points-dapparitions)
  - [wowhead.com](https://fr.wowhead.com/)


Extract data:
> open inspector at https://www.wowhead.com/npc=174054 and run this script:
```js
Promise.all([
  'https://www.wowhead.com/npc=174054',
  'https://www.wowhead.com/npc=174053',
  'https://www.wowhead.com/npc=174052',
  'https://www.wowhead.com/npc=174051',
  'https://www.wowhead.com/npc=174050',
  'https://www.wowhead.com/npc=174049',
  'https://www.wowhead.com/npc=174066',
  'https://www.wowhead.com/npc=174065',
  'https://www.wowhead.com/npc=174064',
  'https://www.wowhead.com/npc=174062',
  'https://www.wowhead.com/npc=174061',
  'https://www.wowhead.com/npc=174048',
  'https://www.wowhead.com/npc=174060',
  'https://www.wowhead.com/npc=174059',
  'https://www.wowhead.com/npc=174058',
  'https://www.wowhead.com/npc=174057',
  'https://www.wowhead.com/npc=174056',
  'https://www.wowhead.com/npc=174055',
  'https://www.wowhead.com/npc=174063',
  'https://www.wowhead.com/npc=174067',
].map(async (url) => {
  const t = await (await fetch(url)).text()
  const list = eval(t.split('\n').find(l => l.includes('WH.TERMS.drops')))
  return [url, list.data.filter(x => x.id !== 183200 && x.id !== 183616).map(x => [x.id, x.name])]
})).then(s => console.log(JSON.stringify(s)))
```
