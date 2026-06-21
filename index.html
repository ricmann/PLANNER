const CACHE='planner-v1';
const ASSETS=[
  '/PLANNER/',
  '/PLANNER/index.html',
  '/PLANNER/manifest.json',
  'https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@latest/tabler-icons.min.css'
];

self.addEventListener('install',e=>{
  e.waitUntil(
    caches.open(CACHE).then(c=>c.addAll(ASSETS)).then(()=>self.skipWaiting())
  );
});

self.addEventListener('activate',e=>{
  e.waitUntil(
    caches.keys().then(keys=>Promise.all(
      keys.filter(k=>k!==CACHE).map(k=>caches.delete(k))
    )).then(()=>self.clients.claim())
  );
});

self.addEventListener('fetch',e=>{
  // Network first for Google Sheets API, cache first for everything else
  if(e.request.url.includes('script.google.com')){
    e.respondWith(fetch(e.request).catch(()=>new Response('{}',{headers:{'Content-Type':'application/json'}})));
    return;
  }
  e.respondWith(
    caches.match(e.request).then(cached=>{
      if(cached)return cached;
      return fetch(e.request).then(resp=>{
        if(resp&&resp.status===200&&resp.type==='basic'){
          const clone=resp.clone();
          caches.open(CACHE).then(c=>c.put(e.request,clone));
        }
        return resp;
      });
    })
  );
});
