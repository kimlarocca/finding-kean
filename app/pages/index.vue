<script setup>
import { ref, computed } from "vue";
import eventsData from "~/assets/events.json";

const showAllEvents = ref(false);
const searchQuery = ref("");

const filteredEvents = computed(() => {
  let events = eventsData;

  // Filter by district if not showing all
  if (!showAllEvents.value) {
    events = events.filter((event) => event.District && event.District.includes("NJ-7"));
  }

  // Filter by search query if provided
  if (searchQuery.value.trim()) {
    const query = searchQuery.value.toLowerCase();
    events = events.filter(
      (event) =>
        event["Event Name"]?.toLowerCase().includes(query) ||
        event.Town?.toLowerCase().includes(query) ||
        event.District?.toLowerCase().includes(query)
    );
  }

  return events;
});

const toggleView = () => {
  showAllEvents.value = !showAllEvents.value;
};

const clearSearch = () => {
  searchQuery.value = "";
};
</script>

<template>
  <div>
    <SectionNav />
    <img
      src="/images/hero.jpg"
      alt="a wheres waldo style image of Tom Kean Jr. hiding in plain sight at various events across NJ-7 | CantFindTom.com | The Investigation into NJ-07's Missing Representative"
      class="w-full mb-16 hidden sm:block"
    />
    <img
      src="/images/hero-mobile.jpg"
      alt="a wheres waldo style image of Tom Kean Jr. hiding in plain sight at various events across NJ-7 | CantFindTom.com | The Investigation into NJ-07's Missing Representative"
      class="w-full mb-16 block sm:hidden"
    />


    <!-- The Intro Section -->
    <section id="the-search" class="container mx-auto p-4">
      <h1 class="mb-6">Tom Kean Jr. —<br />Representative In Title Only</h1>
      <h2 class="like-h3 mb-4">While Tom stays hidden, you pay the price.</h2>
      <p>
        Since he vanished, NJ-7 has been hit with a
        <span class="font-bold">$1.50 gas surcharge</span>, a
        <span class="font-bold">$1,850 healthcare tax</span>, and a militarized agenda for
        a
        <a
          class="font-bold underline"
          href="https://www.wuwf.org/2026-04-29/the-iran-war-now-has-a-price-tag-25-billion-but-still-no-end-date"
          target="_blank"
          >25 Billion war in Iran</a
        >
        without an exit. Tom traded his family legacy for total obedience to his
        <span class="font-bold">New Daddy</span>. He didn't just abandon his seat. He sold
        you out.
      </p>
    </section>

    <!-- The Absence Section -->
    <section id="the-absence" class="container mx-auto p-4 max-w-6xl pt-16 pb-24">
      <img
        src="/images/roxbury-concentration-camp-facility.jpg"
        alt="A photo of the 10-football-field industrial warehouse in Roxbury. A bronze-style plaque graphic is overlaid: 'THE KEAN FAMILY HUMAN WAREHOUSE | A Monument to Feckless Silence and Disappearing Representation.'"
        class="w-full mb-12 hidden sm:block"
      />
      <img
        src="/images/roxbury-concentration-camp-facility-mobile.jpg"
        alt="A photo of the 10-football-field industrial warehouse in Roxbury. A bronze-style plaque graphic is overlaid: 'THE KEAN FAMILY HUMAN WAREHOUSE | A Monument to Feckless Silence and Disappearing Representation.'"
        class="w-full mb-12 block sm:hidden"
      />

      <div class="section-label">Section 1 — The Absence</div>
      <div class="missing-flyer mb-8">
        <div class="missing-flyer-header">🔍 Missing Person Report</div>
        <div class="missing-flyer-body">
          <h2 class="mb-6">The MIA Report</h2>
          <ul class="space-y-4 list-disc ml-5 mb-8">
        <li>
          <strong>Last Seen in Public:</strong> Tom hasn't held an open-to-the-public town
          hall in over 3 years.
        </li>
        <li>
          <strong>75+ Missed Votes:</strong> Since March 5, 2026, Tom has been a total
          no-show.
          <a
            href="https://www.njspotlightnews.org/2026/04/radio-silence-concerns-grow-about-congressmans-health-during-lengthy-absence/"
            target="_blank"
            >Constituents and colleagues alike are met with radio silence.</a
          >
        </li>
        <li>
          <strong>The 53-Day Silence:</strong> It took nearly two months before
          <a
            href="https://www.insidernj.com/tom-kean-speaks-about-his-absence/"
            target="_blank"
            >his team released a single, vague statement</a
          >
          that refused to disclose the nature of his absence.
        </li>
        <li>
          <strong>Selective Recovery:</strong> While "too ill" to vote, he
          <a
            href="https://dccc.org/breaking-rep-tom-kean-jr-has-disappeared-from-capitol-hill-hes-still-trading-stocks-notus/"
            target="_blank"
            >personally certified $190,000 in stock trades</a
          >
          during the height of his absence.
        </li>
          </ul>
        </div>
      </div>
      <div class="stripe-accent"></div>
      <h3 class="mb-3">A Legacy of Silence</h3>
      <p>
        Long before his current disappearance, Tom was already missing on the issues that
        matter. When the federal government fast-tracked the Roxbury Human Warehouse, Tom
        stood by and did nothing. Because of his feckless silence, this industrial
        disaster is now the physical monument to his failure. Junior has traded the
        moderation of his father for total obedience to his "New Daddy" in Washington. He
        has not only abandoned NJ-7—he has tarnished a family legacy that spans 250 years.
      </p>
    </section>

    <div class="waldo-divider" />

    <!-- The Paper Trail Section -->
    <section id="the-record" class="container mx-auto p-4 max-w-6xl py-24">
      <div class="section-label">Section 2 — The Paper Trail</div>
      <h2 class="mb-4">The Price of His Silence</h2>
      <div class="stripe-accent"></div>
      <h3 class="mb-6">The PaPer Trail</h3>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-12">
        <!-- Card: DEBT -->
        <div
          class="p-16 relative bg-cover bg-center bg-no-repeat"
          style="background-image: url('/images/ripped-case-file-background.jpg')"
        >
          <div class="card-stripe-header"></div>
          <span
            class="absolute top-4 right-4 text-2xl font-black text-white bg-red-600 px-4 py-2 rotate-[-8deg] inline-block"
            >DEBT</span
          >
          <h4 class="font-bold mb-2 bg-stone-300 p-1 pb-2 w-fit">The Deficit Bomb</h4>
          <p class="font-semibold">
            Tom was a key vote for the
            <a
              href="https://www.appropriations.senate.gov/news/minority/senator-murray-asks-cbo-about-impact-of-trumps-defense-budget-on-deficits"
              target="_blank"
              >Big Ugly Bill (BUB)</a
            >. Ballooned the deficit by $4.7 Trillion. You pay for his optics every time
            you buy groceries.
          </p>
        </div>
        <!-- Card: TAX -->
        <div
          class="p-16 relative bg-cover bg-center bg-no-repeat"
          style="background-image: url('/images/ripped-case-file-background.jpg')"
        >
          <div class="card-stripe-header"></div>
          <span
            class="absolute top-4 right-4 text-2xl font-black text-white bg-red-600 px-4 py-2 rotate-[-8deg] inline-block"
            >TAX</span
          >
          <h4 class="font-bold mb-2 bg-stone-300 p-1 pb-2 w-fit">
            The Iran War Surcharge
          </h4>
          <p class="font-semibold">
            While Tom was MIA, his office cheered for a war that has cost taxpayers
            <a
              href="https://www.wuwf.org/2026-04-29/the-iran-war-now-has-a-price-tag-25-billion-but-still-no-end-date"
              target="_blank"
              >$25 Billion</a
            >. You are paying a $1.50/gallon War Tax at the pump.
          </p>
        </div>
        <!-- Card: DUMB -->
        <div
          class="p-16 relative bg-cover bg-center bg-no-repeat"
          style="background-image: url('/images/ripped-case-file-background.jpg')"
        >
          <div class="card-stripe-header"></div>
          <span
            class="absolute top-4 right-4 text-2xl font-black text-white bg-red-600 px-4 py-2 rotate-[-8deg] inline-block"
            >DUMB</span
          >
          <h4 class="font-bold mb-2 bg-stone-300 p-1 pb-2 w-fit">Killing the Future</h4>
          <p class="font-semibold">
            Tom started as an EPA advisor but voted to
            <a href="https://www.lcv.org/moc/thomas-kean/" target="_blank"
              >kill solar subsidies</a
            >, keeping us dependent on volatile oil as rates surged 20%.
          </p>
        </div>
        <!-- Card: CUT -->
        <div
          class="p-16 relative bg-cover bg-center bg-no-repeat"
          style="background-image: url('/images/ripped-case-file-background.jpg')"
        >
          <div class="card-stripe-header"></div>
          <span
            class="absolute top-4 right-4 text-2xl font-black text-white bg-red-600 px-4 py-2 rotate-[-8deg] inline-block"
            >CUT</span
          >
          <h4 class="font-bold mb-2 bg-stone-300 p-1 pb-2 w-fit">
            The Healthcare Betrayal
          </h4>
          <p class="font-semibold">
            Tom's BUB vote
            <a
              href="https://dccc.org/nearly-70000-new-jerseyans-going-uninsured-because-of-tom-kean-jr/"
              target="_blank"
              >stripped protection from 70,000 residents</a
            >
            in NJ-7. Local families pay an average of $1,850 more per year.
          </p>
        </div>
      </div>
      <h3 class="mb-3">The Out-of-Touch Heir</h3>
      <p>
        Tom Kean Jr. is a wealthy heir whose family name is plastered on buildings across
        NJ. He is a pawn who used a family legacy to secure a seat he is unqualified to
        hold. He isn't working for you. He is just waiting for his next instruction from
        his new daddy.
      </p>
    </section>

    <!-- The Power Vacuum Section -->
    <section id="autopilot-rep" class="w-full bg-stone-900 text-white">
      <div class="container mx-auto p-4 max-w-6xl py-24">
        <div class="section-label section-label--white">Section 3 — The Power Vacuum</div>
        <h2 class="mb-4 text-white">Who is Pulling the Strings?</h2>
        <div class="stripe-accent mb-12"></div>
        <div class="flex flex-col md:flex-row gap-10 items-start">
          <img
            src="/images/the-power-vacuum.jpg"
            alt="Who is Pulling the Strings?"
            class="w-full md:w-1/2 object-cover md:order-last"
          />
          <div class="flex-1">
            <h3 class="mb-12 text-white">The Power Vacuum</h3>
            <ul class="space-y-4 list-disc ml-5">
              <li>
                <strong>The Proxy Portfolio:</strong> While too ill to vote for NJ-7, Tom
                <a
                  href="https://www.notus.org/congress/tom-kean-trading-stocks"
                  target="_blank"
                  class="text-white underline"
                  >certified $190,000 in private stock trades</a
                >
                (J&amp;J, PepsiCo) between March 10 and 31.
              </li>
              <li>
                <strong>The Blind Trust Lie:</strong> In 2024, Tom
                <a
                  href="https://www.pbs.org/video/riley-yates-intv-1753467685/"
                  target="_blank"
                  class="text-white underline"
                  >pledged on camera to put his assets in a blind trust</a
                >. He broke that promise.
              </li>
              <li>
                <strong>The Ghost Rep:</strong> Even colleagues reported "radio silence."
                We are being managed by a machine that prioritizes the Kean family's
                bottom line.
              </li>
              <li>
                <strong>Weekend at Bernie's:</strong> His staff won't say what is wrong.
                Are the statements coming from Tom, or is he just a pawn waiting for
                instructions from Tom's new daddy?
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Tom's 2 Daddies Section -->
    <section id="toms-2-daddies" class="container mx-auto p-4 max-w-6xl py-24">
      <div class="section-label">Section 4 — Tom's 2 Daddies</div>
      <h2 class="mb-4">Tom's 2 Daddies</h2>
      <div class="stripe-accent mb-12"></div>
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-12">
        <!-- Tom Kean Sr. -->
        <div class="border-2 border-gray-300 dark:border-stone-900 p-8">
          <h3 class="mb-2 text-center text-red-600">Tom Kean Sr.</h3>
          <h4 class="text-center text-red-600 mb-6">The Moderate</h4>
          <dl class="space-y-6">
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1">
                The Philosophy
              </dt>
              <dd>
                <a
                  href="https://governors.rutgers.edu/governor-thomas-h-kean-archive/"
                  target="_blank"
                  class="underline"
                  ><strong>Inclusion.</strong></a
                >
                Wrote the book on the "Politics of Inclusion," uniting NJ.
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1">The Conduct</dt>
              <dd>
                <a
                  href="https://governors.rutgers.edu/kean-byrne-dialogues/"
                  target="_blank"
                  class="underline"
                  ><strong>Civility.</strong></a
                >
                Decades of bipartisanship. Politics doesn't have to be a "dirty business."
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1">The Legacy</dt>
              <dd>
                <a
                  href="https://governors.rutgers.edu/wp-content/uploads/2020/06/kean_speech_1985-08-20_Divestiture.pdf"
                  target="_blank"
                  class="underline"
                  ><strong>Morality.</strong></a
                >
                Risked political capital to fight Apartheid by divesting NJ funds.
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1">The Earth</dt>
              <dd>
                <a
                  href="https://governors.rutgers.edu/thomas-h-kean-administration-environment-timeline/"
                  target="_blank"
                  class="underline"
                  ><strong>Conservation.</strong></a
                >
                Championed efforts to clean up NJ's toxic waste sites.
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1">The Law</dt>
              <dd>
                <a
                  href="https://www.insidernj.com/the-condemnation-of-trump-by-kean-sr-and-the-dilemma-it-poses-for-junior/"
                  target="_blank"
                  class="underline"
                  ><strong>Order.</strong></a
                >
                Defended the Constitution after the January 6th attack.
              </dd>
            </div>
          </dl>
        </div>
        <!-- Donald Trump -->
        <div class="border-2 border-red-600 bg-stone-900 text-white p-8">
          <h3 class="mb-2 text-center text-white">Donald Trump</h3>
          <h4 class="text-center text-white mb-6">The Extremist</h4>
          <dl class="space-y-6">
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1 text-red-400">
                The Philosophy
              </dt>
              <dd>
                <a
                  href="https://en.wikipedia.org/wiki/Targeting_of_political_opponents_and_civil_society_under_the_second_Trump_administration/"
                  class="underline text-white"
                  ><strong>Revenge.</strong></a
                >
                Running a
                <a
                  href="https://fipa.bc.ca/nm/justice-department-escalates-scrutiny-of-trump-foes-with-probes-of-letitia-james-and-adam-schiff/"
                  class="underline text-white"
                  >retribution campaign.</a
                >
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1 text-red-400">
                The Conduct
              </dt>
              <dd>
                <a
                  href="https://www.voanews.com/a/transcript-of-donald-trumps-conversation-with-billy-bush-of-access-hollywood/3542128.html"
                  class="underline text-white"
                  ><strong>Contempt.</strong></a
                >
                "Grab 'em by the pussy." The gold standard for toxic conduct.
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1 text-red-400">
                The Legacy
              </dt>
              <dd>
                <strong>Greed.</strong> Gained
                <a
                  href="https://time.com/7342470/trump-net-worth-wealth-crypto/"
                  class="underline text-white"
                  >$3.4 Billion in wealth</a
                >
                while in office.
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1 text-red-400">
                The Earth
              </dt>
              <dd>
                <strong>Exploitation.</strong> Dismantled climate protections and
                <a
                  href="https://biologicaldiversity.org/w/news/press-releases/trump-proposes-opening-over-1-million-acres-of-california-public-lands-to-drilling-fracking-2026-01-12/"
                  class="underline text-white"
                  >opened public lands to drilling.</a
                >
              </dd>
            </div>
            <div>
              <dt class="font-black uppercase tracking-wide text-sm mb-1 text-red-400">
                The Law
              </dt>
              <dd>
                <strong>Chaos.</strong> Attempted to steal the 2020 election and
                <a
                  href="https://19thnews.org/2026/01/january-6-pardons-arrests/"
                  class="underline text-white"
                  >pardoned the criminals</a
                >
                who re-offended.
              </dd>
            </div>
          </dl>
        </div>
      </div>
      <div class="border-l-4 border-red-600 pl-6">
        <p>
          <strong>The Bottom Line:</strong> Tom Kean Sr. stood for the Politics of
          Inclusion. Tom Jr. is an absentee lap dog for Trump. Whatever his mystery
          medical ailment, let's hope he is undergoing a
          <strong>Transverse Vertebral Augmentation</strong> to finally give him a spine.
          He isn't just sick. He's been missing for years. His family should be ashamed of
          him.
        </p>
      </div>
    </section>

    <div class="waldo-divider" />

    <section class="container mx-auto p-4 max-w-6xl py-24">
      <NewsletterSignup />
    </section>

    <div class="waldo-divider" />

    <!-- The Partners Section -->
    <section class="container mx-auto p-4 max-w-6xl pt-16">
      <h2 class="mb-6">Partners & Sponsors</h2>
      <div class="flex flex-col sm:flex-row md:items-center gap-8 sm:gap-12">
        <a
          href="https://www.facebook.com/FindingKean2025/"
          target="_blank"
          rel="noopener noreferrer"
          class="plain"
        >
          <img
            src="/images/finding-kean-fridays.png"
            alt="Finding Kean Fridays"
            class="w-64 h-64 object-contain"
          />
        </a>
        <a
          href="https://www.papnj.com"
          target="_blank"
          rel="noopener noreferrer"
          class="plain"
        >
          <img
            src="/images/pap.png"
            alt="People Are People - New Jersey"
            class="w-64 h-64 object-contain"
          />
        </a>
        <a
          href="https://www.onenj7.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="plain"
        >
          <img
            src="/images/onenj.jpg"
            alt="One NJ 7"
            class="w-64 h-64 object-contain"
          />
        </a>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
.waldo-divider {
  height: 24px;
  background: repeating-linear-gradient(
    to right,
    #cc0000 0px,
    #cc0000 24px,
    #ffffff 24px,
    #ffffff 48px
  );
  width: 100%;
}

.section-label {
  display: inline-block;
  font-family: var(--font-family-header);
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #ffffff;
  background: #cc0000;
  padding: 3px 10px;
  margin-bottom: 12px;

  &.section-label--white {
    background: #ffffff;
    color: #cc0000;
  }
}

.stripe-accent {
  height: 8px;
  background: repeating-linear-gradient(
    to right,
    #cc0000 0px,
    #cc0000 12px,
    #ffffff 12px,
    #ffffff 24px
  );
  width: 80px;
  margin-bottom: 24px;
  margin-top: 4px;
}

.missing-flyer {
  border: 3px solid #cc0000;

  .missing-flyer-header {
    background: #cc0000;
    color: #ffffff;
    font-family: var(--font-family-header);
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.2em;
    text-align: center;
    padding: 8px 16px;
    font-size: 14px;
  }

  .missing-flyer-body {
    padding: 24px;
  }
}

.card-stripe-header {
  height: 12px;
  background: repeating-linear-gradient(
    to right,
    #cc0000 0px,
    #cc0000 12px,
    #ffffff 12px,
    #ffffff 24px
  );
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
}
</style>
