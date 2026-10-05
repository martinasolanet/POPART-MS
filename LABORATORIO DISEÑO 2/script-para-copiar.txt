const obras = [
  {
    title: 'F-111',
    artist: 'James Rosenquist',
    year: '1964–1965',
    description: 'Esta pintura monumental muestra un avión de combate F-111 atravesando imágenes de productos y escenas cotidianas. Rosenquist la diseñó para rodear al espectador por las cuatro paredes de una galería, como una publicidad imposible de ignorar.',
    detail: 'Clave de la obra: el choque entre consumo y armamento invita a pensar en la sociedad estadounidense durante la guerra de Vietnam.'
  },
  {
    title: 'Gold Marilyn Monroe',
    artist: 'Andy Warhol',
    year: '1962',
    description: 'El rostro de Marilyn Monroe, tomado de una fotografía publicitaria de la película Niagara, aparece aislado sobre un gran fondo dorado. Warhol realizó la obra en el año de la muerte de la actriz.',
    detail: 'Clave de la obra: el fondo recuerda a los íconos religiosos mientras la imagen reproducida habla de fama y cultura de masas.'
  },
  {
    title: 'Giant BLT (Bacon, Lettuce, and Tomato Sandwich)',
    artist: 'Claes Oldenburg',
    year: '1963',
    description: 'Oldenburg convirtió un sándwich BLT en una escultura de tamaño desmesurado. Combinó materiales blandos con elementos rígidos para que un alimento familiar se viera insólito y casi teatral.',
    detail: 'Clave de la obra: agrandar y transformar la comida cotidiana cambia nuestra manera de mirarla.'
  },
  {
    title: 'The Toy Shop',
    artist: 'Peter Blake',
    year: '1962',
    description: 'Blake construyó una tienda de juguetes como un relieve lleno de objetos, figuras y recuerdos. La obra parece un escaparate que mezcla colección personal y cultura popular británica.',
    detail: 'Clave de la obra: los objetos reales y su presentación comercial entran directamente en el lenguaje del arte.'
  },
  {
    title: 'Girl in Window (Study for World’s Fair Mural)',
    artist: 'Roy Lichtenstein',
    year: '1963',
    description: 'Una mujer sonriente se asoma a una ventana verde. Lichtenstein realizó esta pintura como estudio para un mural destinado a la Feria Mundial de Nueva York de 1964.',
    detail: 'Clave de la obra: los contornos gruesos, colores planos y puntos Ben-Day imitan la impresión comercial y acercan la pintura a la historieta.'
  },
  {title:'Drowning Girl',artist:'Roy Lichtenstein',year:'1963',description:'Una mujer aparece entre olas y un globo de diálogo, como en una viñeta melodramática. Lichtenstein aísla y amplía la escena para que contemplemos sus emociones y su modo de impresión.',detail:'Clave de la obra: los puntos Ben-Day y el texto convierten una imagen de historieta en una pintura de museo.'},
  {title:'LOVE',artist:'Robert Indiana',year:'1966',description:'Las cuatro letras de la palabra LOVE están apiladas en un cuadrado y la O se inclina hacia la derecha. La composición se volvió inmediatamente reconocible y circuló después en impresiones y esculturas.',detail:'Clave de la obra: usa una palabra breve como imagen, con la fuerza gráfica de un cartel.'},
  {title:'A Bigger Splash',artist:'David Hockney',year:'1967',description:'Una piscina californiana aparece bajo un cielo sereno. El agua salta por los aires, pero la persona que acaba de lanzarse queda fuera de cuadro; el cuadro congela un instante fugaz.',detail:'Clave de la obra: las superficies lisas y el contraste entre quietud y movimiento evocan las imágenes de ocio de la época.'},
  {title:'I Was a Rich Man’s Plaything',artist:'Eduardo Paolozzi',year:'1947',description:'Paolozzi compuso este collage con recortes de revistas y anuncios estadounidenses. Entre sus imágenes de consumo aparecen productos, figuras y la palabra «POP» junto a un arma de juguete.',detail:'Clave de la obra: anticipa el vocabulario visual del Pop Art antes de que el movimiento recibiera ese nombre.'},
  {title:'Great American Nude, #57',artist:'Tom Wesselmann',year:'1964',description:'Wesselmann combina una figura femenina con elementos de un interior doméstico en una composición de grandes áreas de color. La obra forma parte de su serie Great American Nude.',detail:'Clave de la obra: mezcla el desnudo de la tradición artística con la estética brillante de anuncios y objetos de consumo.'}
];
const galeriaObras = [
  {title:'Brillo Soap Pads Box',artist:'Andy Warhol',year:'1964'},
  {title:'Flowers',artist:'Andy Warhol',year:'1964'},
  {title:'Look Mickey',artist:'Roy Lichtenstein',year:'1961'},
  {title:'Girl with Hair Ribbon',artist:'Roy Lichtenstein',year:'1965'},
  {title:'Glass Case with Pies',artist:'Claes Oldenburg',year:'1962'},
  {title:'Lipstick (Ascending) on Caterpillar Tracks',artist:'Claes Oldenburg',year:'1969'},
  {title:'Still Life #30',artist:'Tom Wesselmann',year:'1963'},
  {title:'On the Balcony',artist:'Peter Blake',year:'1955–1957'},
  {title:'The Family',artist:'Marisol',year:'1962'},
  {title:'Soft Screw',artist:'Claes Oldenburg',year:'1976'}
];
const worksGrid = document.querySelector('#works-grid');
const galleryGrid = document.querySelector('#gallery-grid');
for(let i=0;i<obras.length;i++){
  const obra=obras[i]; const numero=String(i+1).padStart(2,'0');
  const button=document.createElement('button');button.type='button';button.className='art-tile';button.dataset.label=`IMG ${numero}`;
  button.setAttribute('aria-label',`Ampliar ${obra.title}`);
  const img=document.createElement('img');img.src=`imagenes/obras-principales/obra-${numero}.jpg`;img.alt=`${obra.title} de ${obra.artist}`;img.loading='lazy';img.addEventListener('error',()=>{img.hidden=true});
  button.append(img);button.addEventListener('click',()=>openArt(i,img.src));worksGrid.append(button);
}
for(let i=0;i<galeriaObras.length;i++){
  const obra=galeriaObras[i];
  const numero=String(i+1).padStart(2,'0');
  const button=document.createElement('button');button.type='button';button.className='gallery-piece';button.dataset.label=`IMG ${numero}`;
  button.setAttribute('aria-label',`Ampliar ${obra.title} de ${obra.artist}`);
  const img=document.createElement('img');img.src=`imagenes/galeria/galeria-${numero}.jpg`;img.alt=`Aquí va ${obra.title}, de ${obra.artist}`;img.loading='lazy';img.addEventListener('error',()=>{img.hidden=true});
  button.append(img);button.addEventListener('click',()=>openGallery(img,obra));galleryGrid.append(button);
}
const modal=document.querySelector('#art-modal');
const modalArt=document.querySelector('#modal-art');
function showModal(word,style,kicker,title,description,detail=''){
  modalArt.className=`modal-art ${style}`; modalArt.replaceChildren();
  const span=document.createElement('span'); span.textContent=word; modalArt.append(span);
  document.querySelector('#modal-kicker').textContent=kicker;
  document.querySelector('#modal-title').textContent=title;
  document.querySelector('#modal-description').textContent=description;
  const detailElement=document.querySelector('#modal-detail'); detailElement.textContent=detail; detailElement.hidden=!detail;
  modal.showModal(); document.querySelector('.modal-close').focus();
}
function showImage(src,alt,kicker,title,description,detail=''){
  showModal('', 'photo-art', kicker,title,description,detail);
  const img=document.createElement('img');
  img.alt=alt;
  img.addEventListener('error',()=>{
    const placeholder=document.createElement('span');
    placeholder.className='modal-missing';
    placeholder.textContent=`Agregá ${src.split('/').pop()} para ver la imagen`;
    modalArt.replaceChildren(placeholder);
  });
  img.src=src;
  modalArt.replaceChildren(img);
}
function openArt(i,src){
  const o=obras[i];
  showImage(src,`${o.title} de ${o.artist}`,`${o.artist.toUpperCase()} · ${o.year}`,o.title,o.description,o.detail);
}
const galleryModal=document.createElement('dialog');
galleryModal.className='gallery-modal';
galleryModal.innerHTML='<button type="button" class="gallery-modal-close" aria-label="Cerrar imagen">×</button><div class="gallery-image-wrap"><img alt=""><span class="gallery-missing" hidden></span></div><div class="gallery-caption"><h2 id="gallery-title"></h2><p id="gallery-year"></p></div>';
document.body.append(galleryModal);
function openGallery(image,obra){
  const enlarged=galleryModal.querySelector('img');
  const missing=galleryModal.querySelector('.gallery-missing');
  galleryModal.querySelector('#gallery-title').textContent=obra.title;
  galleryModal.querySelector('#gallery-year').textContent=obra.year;
  missing.textContent=`Agregá ${image.src.split('/').pop()} para ver la imagen`;
  missing.hidden=!image.hidden;
  enlarged.hidden=image.hidden;
  enlarged.src=image.src;
  enlarged.alt=image.alt;
  enlarged.onerror=()=>{enlarged.hidden=true;missing.hidden=false};
  galleryModal.showModal();
  galleryModal.querySelector('.gallery-modal-close').focus();
}
galleryModal.querySelector('.gallery-modal-close').addEventListener('click',()=>galleryModal.close());
galleryModal.addEventListener('click',event=>{if(event.target===galleryModal)galleryModal.close()});
const obrasArtistas={
  warhol:{src:'imagenes/obras/campbells-soup-cans.jpg',title:'Campbell’s Soup Cans',artist:'Andy Warhol',year:'1962',description:'Treinta y dos lienzos presentan variedades de sopa Campbell. Warhol convirtió un producto de supermercado en una imagen repetida y digna de museo.'},
  lichtenstein:{src:'imagenes/obras/whaam.jpg',title:'Whaam!',artist:'Roy Lichtenstein',year:'1963',description:'Dos paneles muestran una escena de combate y una explosión. Lichtenstein lleva el lenguaje de la historieta a la escala de una pintura monumental.'},
  hamilton:{src:'imagenes/obras/just-what-is-it.jpg',title:'Just what is it...',artist:'Richard Hamilton',year:'1956',description:'Un collage de recortes publicitarios y objetos de consumo llena un interior doméstico y anticipa la estética del Pop Art británico.'},
  oldenburg:{src:'imagenes/obras/floor-burger.jpg',title:'Floor Burger',artist:'Claes Oldenburg',year:'1962',description:'Una hamburguesa blanda y enorme transforma un alimento cotidiano en una escultura sorprendente.'}
};
document.querySelectorAll('.artist-work').forEach(button=>button.addEventListener('click',()=>{
  const obra=obrasArtistas[button.dataset.artist];
  showImage(obra.src,`${obra.title} de ${obra.artist}`,`${obra.artist.toUpperCase()} · ${obra.year}`,obra.title,obra.description);
}));
document.querySelector('.modal-close').addEventListener('click',()=>modal.close());
modal.addEventListener('click',event=>{if(event.target===modal)modal.close()});
const toggle=document.querySelector('.menu-toggle');const nav=document.querySelector('.nav');
toggle.addEventListener('click',()=>{const open=nav.classList.toggle('open');toggle.setAttribute('aria-expanded',String(open))});
document.querySelectorAll('.nav a').forEach(link=>link.addEventListener('click',()=>{nav.classList.remove('open');toggle.setAttribute('aria-expanded','false')}));
const links=[...document.querySelectorAll('.nav a')];
const observer=new IntersectionObserver(entries=>{
  const visible=entries.filter(e=>e.isIntersecting).sort((a,b)=>b.intersectionRatio-a.intersectionRatio)[0];
  if(!visible)return;links.forEach(a=>{const active=a.getAttribute('href')===`#${visible.target.id}`;a.classList.toggle('active',active);if(active)a.setAttribute('aria-current','location');else a.removeAttribute('aria-current')});
},{rootMargin:'-25% 0px -50% 0px',threshold:[0,.1,.25,.5]});
document.querySelectorAll('main section:not(#inicio)').forEach(section=>observer.observe(section));
document.querySelector('#contact-form').addEventListener('submit',event=>{
  event.preventDefault();const data=new FormData(event.currentTarget);
  const emailDestino=''; // Escribí acá tu correo, por ejemplo: 'hola@tudominio.com'
  const subject=encodeURIComponent(`Mensaje desde POP! de ${data.get('nombre')}`);
  const body=encodeURIComponent(`Nombre: ${data.get('nombre')}\nEmail: ${data.get('email')}\n\n${data.get('mensaje')}`);
  window.location.href=`mailto:${emailDestino}?subject=${subject}&body=${body}`;
});
