# Kontakt in povpraševanje

<!-- opis: Pošljite povpraševanje za sobo ali apartma v Bohinju: datumi, število oseb in želena nastanitev. Odgovorimo v enem dnevu. Demo stran. -->

<div class="contact-layout">
  <div>
    <p class="lead">Napišite nam datume in število oseb, pa vam v enem dnevu potrdimo prost termin in končno ceno. Povpraševanje ni zavezujoče.</p>
    <div class="contact-buttons">
      <a class="btn" href="tel:{{ site.phone }}">Pokliči {{ site.phone_display }}</a>
      <a class="btn btn-whatsapp" href="https://wa.me/{{ site.whatsapp }}?text=Pozdravljeni%2C%20zanima%20me%20prost%20termin." rel="noopener">WhatsApp</a>
      <a class="btn btn-ghost" href="mailto:{{ site.email }}">{{ site.email }}</a>
    </div>
    <p><strong>Naslov:</strong> {{ site.location }}<br>Natančna navodila za prihod pošljemo ob potrditvi rezervacije.</p>
  </div>
  <form id="povprasevanje" class="inquiry-form" action="#povprasevanje" method="POST" data-demo>
    <label>Ime in priimek *<input type="text" name="ime" autocomplete="name" required></label>
    <div class="form-row">
      <label>E-pošta *<input type="email" name="email" autocomplete="email" required></label>
      <label>Telefon<input type="tel" name="telefon" autocomplete="tel" inputmode="tel"></label>
    </div>
    <div class="form-row">
      <label>Prihod *<input type="date" name="prihod" id="prihod" required></label>
      <label>Odhod *<input type="date" name="odhod" id="odhod" required></label>
    </div>
    <div class="form-row">
      <label>Odrasli *<input type="number" name="odrasli" min="1" max="5" value="2" inputmode="numeric" required></label>
      <label>Otroci<input type="number" name="otroci" min="0" max="4" value="0" inputmode="numeric"></label>
    </div>
    <label>Nastanitev<select name="nastanitev"><option>Vseeno, predlagajte</option><option>Soba z balkonom</option><option>Družinska soba</option><option>Studio Savica</option><option>Apartma Vogel</option></select></label>
    <label>Sporočilo (zajtrk, hišni ljubljenček, pozen prihod ...)<textarea name="sporocilo" rows="4"></textarea></label>
    <button class="btn" type="submit">Pošlji povpraševanje</button>
    <p class="form-note">Odgovorimo v enem dnevu. Rezervacija je potrjena šele z našim odgovorom.</p>
    <p class="form-demo-msg" id="demo-msg" hidden>To je demo: obrazec ne pošilja. Na pravi strani bi povpraševanje prispelo na e-pošto gostiteljev.</p>
  </form>
</div>
<script>
  (function () {
    function iso(d) { return d.toISOString().slice(0, 10); }
    var prihod = document.getElementById("prihod");
    var odhod = document.getElementById("odhod");
    var danes = new Date();
    prihod.min = iso(danes);
    odhod.min = iso(new Date(danes.getTime() + 864e5));
    // Odhod je vsaj dan po prihodu.
    prihod.addEventListener("change", function () {
      if (!prihod.value) return;
      var naslednji = new Date(new Date(prihod.value).getTime() + 864e5);
      odhod.min = iso(naslednji);
      if (!odhod.value || odhod.value <= prihod.value) odhod.value = iso(naslednji);
    });
    document.getElementById("povprasevanje").addEventListener("submit", function (e) {
      e.preventDefault();
      document.getElementById("demo-msg").hidden = false;
    });
  })();
</script>
