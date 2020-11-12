# icecrown
*interactive spawn map*
----

Data source:
  - [mamytwink.com](https://www.mamytwink.com/actualite/invasion-du-fleau-horaires-de-lapparition-des-boss-de-la-couronne-de-glace#points-dapparitions)
  - [wowhead.com](https://fr.wowhead.com/)


Extract data:
```js
Promise.all([
  'https://en.wowhead.com/npc=174054',
  'https://en.wowhead.com/npc=174053',
  'https://en.wowhead.com/npc=174052',
  'https://en.wowhead.com/npc=174051',
  'https://en.wowhead.com/npc=174050',
  'https://en.wowhead.com/npc=174049',
  'https://en.wowhead.com/npc=174066',
  'https://en.wowhead.com/npc=174065',
  'https://en.wowhead.com/npc=174064',
  'https://en.wowhead.com/npc=174062',
  'https://en.wowhead.com/npc=174061',
  'https://en.wowhead.com/npc=174048',
  'https://en.wowhead.com/npc=174060',
  'https://en.wowhead.com/npc=174059',
  'https://en.wowhead.com/npc=174058',
  'https://en.wowhead.com/npc=174057',
  'https://en.wowhead.com/npc=174056',
  'https://en.wowhead.com/npc=174055',
  'https://en.wowhead.com/npc=174063',
  'https://en.wowhead.com/npc=174067',
].map(async (url) => {
  const t = await (await fetch(url)).text()
  const list = eval(t.split('\n').find(l => l.includes('WH.TERMS.drops')))
  return [url, list.data.filter(x => x.id !== 183200 && x.id !== 183616).map(x => [x.id, x.name, x.quality])]
})).then(s => console.log(JSON.stringify(s)))
```
