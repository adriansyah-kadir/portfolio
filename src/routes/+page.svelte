<script lang="ts">
  import List from "$lib/components/list.svelte";

  const contacts = [
    {
      label: "Whatsapp",
      link: "https://wa.me/+6285256860481",
    },
    {
      label: "Email",
      link: "mailto:adriansyahkadir.work@gmail.com",
    },
    {
      label: "Github",
      link: "https://github.com/adriansyah-kadir?tab=repositories",
    },
  ];

  const roles = [
    "Software Developer",
    "IT Support",
    "Backend & Computer Vision",
  ];

  const experiences = [
    {
      job: "Software Developer",
      company: "Kejaksaan Negeri Kota Gorontalo",
      desc: "Mengembangkan 4 aplikasi end-to-end untuk kebutuhan operasional, meliputi absensi face recognition, sistem barang bukti QR Code, sistem surat masuk dan keluar, serta survei kepuasan pelayanan. Terlibat dalam analisis kebutuhan hingga implementasi dan berkolaborasi dengan berbagai bidang untuk menyesuaikan aplikasi dengan alur operasional masing-masing.",
      start: new Date("2024 1 Jan"),
      end: new Date("2024 1 May"),
    },
    {
      job: "IT Support (Infra)",
      company: "Universitas Muhammadiyah Gorontalo",
      desc: "Menangani instalasi AP dan CCTV, pemasangan LAN dan fiber optic antar fakultas, serta troubleshooting dan pemeliharaan perangkat dan infrastruktur jaringan kampus.",
      start: new Date("2025 24 Dec"),
      end: new Date("2026 22 May"),
    },
  ];
</script>

<div id="cv" class="max-w-4xl m-auto *:my-6 p-5">
  {@render Header()}

  <hr class="border-primary border-2" />

  {@render Profile()}

  {@render Experience()}

  <section>
    {@render SectionTitle("Pendidikan & Sertifikasi")}
    <div class="flex flex-col sm:flex-row *:w-full gap-5">
      {@render Pendidikan()}
      {@render Sertifikasi()}
    </div>
  </section>

  {@render Skills()}
</div>

{#snippet Header()}
  <section class="grid sm:grid-cols-[auto_1fr] tems-center">
    <img
      class="rounded-full size-26 object-cover row-span-999 sm:mr-5 sm:mb-0 mb-5"
      alt="Profile"
      src="pas-foto.jpg"
    />
    <h2 class="text-2xl font-bold text-primary">Adriansyah Kadir</h2>
    <List class="text-lg font-bold" items={roles}>
      {#snippet children(role)}
        {role}
      {/snippet}
    </List>
    <small>Gorontalo, Indonesia</small>
    <List class="flex gap-1 items-center" items={contacts} separator="·">
      {#snippet children(contact)}
        {#if typeof contact === "string"}
          {contact}
        {:else}
          <a class="underline text-secondary" href={contact.link}
            >{contact.label}</a
          >
        {/if}
      {/snippet}
    </List>
  </section>
{/snippet}

{#snippet Profile()}
  <section>
    {@render SectionTitle("Profil")}
    <p class="text-justify">
      Sarjana Teknik Informatika dengan pengalaman dalam software development,
      IT infrastructure, dan computer vision. Berpengalaman mengembangkan
      aplikasi web dan mobile serta menangani troubleshooting perangkat dan
      jaringan. Memiliki fokus pada backend development, database, dan computer
      vision, dengan pengalaman menggunakan berbagai teknologi modern untuk
      membangun solusi berbasis teknologi.
    </p>
  </section>
{/snippet}

{#snippet Experience()}
  <section>
    {@render SectionTitle("Pengalaman Kerja")}
    <List class="grid sm:grid-cols-[25%_75%] mt-5" items={experiences}>
      {#snippet separator()}
        <hr class="border-base-300 border-px sm:col-span-2 my-4" />
      {/snippet}
      {#snippet children(ex)}
        {@const start = ex.start.toLocaleDateString("id", {
          month: "short",
          year: "numeric",
        })}
        {@const end = ex.end.toLocaleDateString("id", {
          month: "short",
          year: "numeric",
        })}
        <small class="sm:row-span-3 pr-5 text-base-content/75 font-semibold">
          {start} - {end}
        </small>
        <h3 class="font-semibold">{ex.job}</h3>
        <p class="font-semibold mb-2">{ex.company}</p>
        <p>{ex.desc}</p>
      {/snippet}
    </List>
  </section>
{/snippet}

{#snippet SectionTitle(title: string)}
  <h2 class="text-xl font-semibold">{title}</h2>
  <hr class="border-base-300 border-px mt-1 mb-2" />
{/snippet}

{#snippet Pendidikan()}
  <section>
    <p class="font-semibold">S1 Teknik Informatika</p>
    <p class="font-semibold">Universitas Ichsan Gorontalo</p>
    <p>Agustus 2021 - April 2025</p>
    <p class="font-semibold">IPK: 3.83 / 4.00</p>
  </section>
{/snippet}

{#snippet Sertifikasi()}
  <section>
    <h3 class="font-semibold">Web Developer</h3>
    <p class="font-semibold">Badan Nasional Sertifikasi Profesi (BNSP)</p>
    <p>Agustus 2025 - Agustus 2028</p>
  </section>
{/snippet}

{#snippet Skills()}
  <section class="[&>p]:mt-2">
    {@render SectionTitle("Keahlian Teknis")}

    <div class="grid grid-cols-2 sm:grid-cols-3 gap-y-4 gap-x-2">
      <div>
        <p class="font-semibold">Languages</p>
        <ul class="*:badge *:badge-primary *:badge-sm">
          <li>Rust</li>
          <li>TypeScript</li>
          <li>Python</li>
          <li>C</li>
        </ul>
      </div>

      <div>
        <p class="font-semibold">Backend & Systems</p>
        <ul class="*:badge *:badge-primary *:badge-sm">
          <li>PostgreSQL</li>
          <li>Axum</li>
          <li>FastAPI</li>
          <li>Supabase</li>
        </ul>
      </div>

      <div>
        <p class="font-semibold">Frontend & Mobile</p>
        <ul class="*:badge *:badge-primary *:badge-sm">
          <li>SvelteKit</li>
          <li>Next.js</li>
          <li>Flutter</li>
        </ul>
      </div>

      <div>
        <p class="font-semibold">Computer Vision</p>
        <ul class="*:badge *:badge-primary *:badge-sm">
          <li>OpenCV</li>
          <li>ONNX</li>
          <li>Face Recognition</li>
        </ul>
      </div>

      <div>
        <p class="font-semibold col-span-2">Infrastructure</p>
        <ul class="*:badge *:badge-primary *:badge-sm">
          <li>Linux</li>
          <li>WebRTC</li>
          <li>LiveKit</li>
        </ul>
      </div>
    </div>
  </section>
{/snippet}
