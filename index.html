import { useState, useEffect, useCallback } from "react";

// ─── SUPABASE ─────────────────────────────────────────────────────────────────
const SB_URL = "https://qisiaxtdvlhilrvnhvhp.supabase.co";
const SB_KEY = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InFpc2lheHRkdmxoaWxydm5odmhwIiwicm9sZSI6ImFub24iLCJpYXQiOjE3Nzk4ODk5NDgsImV4cCI6MjA5NTQ2NTk0OH0.QlDiHssYS7NovIApiD-NPhcNQWZL0QWHBRkxqNfn8So";

async function sbFetch(path, method="GET", body=null) {
  const headers = {
    "apikey": SB_KEY,
    "Authorization": "Bearer " + SB_KEY,
    "Content-Type": "application/json",
  };
  if (method==="POST") headers["Prefer"] = "resolution=merge-duplicates,return=representation";
  if (method==="GET") headers["Prefer"] = "return=representation";
  const opts = { method, headers };
  if (body) opts.body = JSON.stringify(body);
  const res = await fetch(SB_URL + "/rest/v1/" + path, opts);
  if (!res.ok) {
    const t = await res.text();
    throw new Error(`${method} ${path}: ${t}`);
  }
  const text = await res.text();
  return text ? JSON.parse(text) : null;
}

const db = {
  async getUsers() { return await sbFetch("users?select=*") || []; },
  async upsertUser(u) { return await sbFetch("users", "POST", u); },
  async deleteUser(id) { return await sbFetch(`users?id=eq.${id}`, "DELETE"); },
  async getLobbies() { return await sbFetch("lobbies?select=*") || []; },
  async upsertLobby(l) { return await sbFetch("lobbies", "POST", l); },
  async getResults() {
    const rows = await sbFetch("results?id=eq.1&select=*");
    return rows?.[0]?.data || {};
  },
  async saveResults(data) {
    return await sbFetch("results", "POST", {id:1, data});
  },
};


// ─── GROUP DATA ───────────────────────────────────────────────────────────────
const GROUPS = {
  A:["Mexico","South Korea","South Africa","Czechia"],
  B:["Canada","Bosnia & Herzegovina","Qatar","Switzerland"],
  C:["Brazil","Morocco","Haiti","Scotland"],
  D:["USA","Paraguay","Australia","Turkey"],
  E:["Germany","Curaçao","Ivory Coast","Ecuador"],
  F:["Netherlands","Japan","Sweden","Tunisia"],
  G:["Belgium","Egypt","Iran","New Zealand"],
  H:["Spain","Cape Verde","Saudi Arabia","Uruguay"],
  I:["France","Senegal","Norway","Iraq"],
  J:["Argentina","Algeria","Austria","Jordan"],
  K:["Portugal","DR Congo","Uzbekistan","Colombia"],
  L:["England","Croatia","Ghana","Panama"],
};
const ALL_TEAMS = Object.values(GROUPS).flat();

const SCHEDULE = [
  {date:"June 11",matches:[{id:"A1",g:"A",home:"Mexico",away:"South Africa"},{id:"A2",g:"A",home:"South Korea",away:"Czechia"}]},
  {date:"June 12",matches:[{id:"B1",g:"B",home:"Canada",away:"Bosnia & Herzegovina"},{id:"D1",g:"D",home:"USA",away:"Paraguay"}]},
  {date:"June 13",matches:[{id:"B2",g:"B",home:"Qatar",away:"Switzerland"},{id:"C1",g:"C",home:"Brazil",away:"Morocco"},{id:"C2",g:"C",home:"Haiti",away:"Scotland"},{id:"D2",g:"D",home:"Australia",away:"Turkey"}]},
  {date:"June 14",matches:[{id:"E1",g:"E",home:"Germany",away:"Curaçao"},{id:"F1",g:"F",home:"Netherlands",away:"Japan"},{id:"E2",g:"E",home:"Ivory Coast",away:"Ecuador"},{id:"F2",g:"F",home:"Sweden",away:"Tunisia"}]},
  {date:"June 15",matches:[{id:"H1",g:"H",home:"Spain",away:"Cape Verde"},{id:"G1",g:"G",home:"Belgium",away:"Egypt"},{id:"H2",g:"H",home:"Saudi Arabia",away:"Uruguay"},{id:"G2",g:"G",home:"Iran",away:"New Zealand"}]},
  {date:"June 16",matches:[{id:"I1",g:"I",home:"France",away:"Senegal"},{id:"I2",g:"I",home:"Iraq",away:"Norway"},{id:"J1",g:"J",home:"Argentina",away:"Algeria"},{id:"J2",g:"J",home:"Austria",away:"Jordan"}]},
  {date:"June 17",matches:[{id:"K1",g:"K",home:"Portugal",away:"DR Congo"},{id:"L1",g:"L",home:"England",away:"Croatia"},{id:"L2",g:"L",home:"Ghana",away:"Panama"},{id:"K2",g:"K",home:"Uzbekistan",away:"Colombia"}]},
  {date:"June 18",matches:[{id:"A3",g:"A",home:"Czechia",away:"South Africa"},{id:"B3",g:"B",home:"Switzerland",away:"Bosnia & Herzegovina"},{id:"B4",g:"B",home:"Canada",away:"Qatar"},{id:"A4",g:"A",home:"Mexico",away:"South Korea"}]},
  {date:"June 19",matches:[{id:"D3",g:"D",home:"USA",away:"Australia"},{id:"C3",g:"C",home:"Scotland",away:"Morocco"},{id:"C4",g:"C",home:"Brazil",away:"Haiti"},{id:"D4",g:"D",home:"Turkey",away:"Paraguay"}]},
  {date:"June 20",matches:[{id:"F3",g:"F",home:"Netherlands",away:"Sweden"},{id:"E3",g:"E",home:"Germany",away:"Ivory Coast"},{id:"E4",g:"E",home:"Ecuador",away:"Curaçao"},{id:"F4",g:"F",home:"Tunisia",away:"Japan"}]},
  {date:"June 21",matches:[{id:"H3",g:"H",home:"Spain",away:"Saudi Arabia"},{id:"G3",g:"G",home:"Belgium",away:"Iran"},{id:"H4",g:"H",home:"Uruguay",away:"Cape Verde"},{id:"G4",g:"G",home:"New Zealand",away:"Egypt"}]},
  {date:"June 22",matches:[{id:"J3",g:"J",home:"Argentina",away:"Austria"},{id:"I3",g:"I",home:"France",away:"Iraq"},{id:"I4",g:"I",home:"Norway",away:"Senegal"},{id:"J4",g:"J",home:"Jordan",away:"Algeria"}]},
  {date:"June 23",matches:[{id:"K3",g:"K",home:"Portugal",away:"Uzbekistan"},{id:"L3",g:"L",home:"England",away:"Ghana"},{id:"L4",g:"L",home:"Croatia",away:"Panama"},{id:"K4",g:"K",home:"Colombia",away:"DR Congo"}]},
  {date:"June 24",matches:[{id:"A5",g:"A",home:"Czechia",away:"Mexico"},{id:"A6",g:"A",home:"South Africa",away:"South Korea"},{id:"B5",g:"B",home:"Switzerland",away:"Canada"},{id:"B6",g:"B",home:"Bosnia & Herzegovina",away:"Qatar"},{id:"C5",g:"C",home:"Scotland",away:"Brazil"},{id:"C6",g:"C",home:"Morocco",away:"Haiti"},{id:"D5",g:"D",home:"Turkey",away:"USA"},{id:"D6",g:"D",home:"Paraguay",away:"Australia"}]},
  {date:"June 25",matches:[{id:"E5",g:"E",home:"Curaçao",away:"Ivory Coast"},{id:"E6",g:"E",home:"Ecuador",away:"Germany"},{id:"F5",g:"F",home:"Japan",away:"Sweden"},{id:"F6",g:"F",home:"Tunisia",away:"Netherlands"},{id:"H5",g:"H",home:"Cape Verde",away:"Saudi Arabia"},{id:"H6",g:"H",home:"Uruguay",away:"Spain"}]},
  {date:"June 26",matches:[{id:"G5",g:"G",home:"Egypt",away:"Iran"},{id:"G6",g:"G",home:"New Zealand",away:"Belgium"},{id:"I5",g:"I",home:"Norway",away:"France"},{id:"I6",g:"I",home:"Senegal",away:"Iraq"},{id:"J5",g:"J",home:"Jordan",away:"Argentina"},{id:"J6",g:"J",home:"Algeria",away:"Austria"}]},
  {date:"June 27",matches:[{id:"K5",g:"K",home:"DR Congo",away:"Uzbekistan"},{id:"K6",g:"K",home:"Colombia",away:"Portugal"},{id:"L5",g:"L",home:"Panama",away:"England"},{id:"L6",g:"L",home:"Croatia",away:"Ghana"}]},
];
const ALL_MATCHES = SCHEDULE.flatMap(d=>d.matches);

const FLAG={"Mexico":"🇲🇽","South Korea":"🇰🇷","South Africa":"🇿🇦","Czechia":"🇨🇿","Canada":"🇨🇦","Bosnia & Herzegovina":"🇧🇦","Qatar":"🇶🇦","Switzerland":"🇨🇭","Brazil":"🇧🇷","Morocco":"🇲🇦","Haiti":"🇭🇹","Scotland":"🏴󠁧󠁢󠁳󠁣󠁴󠁿","USA":"🇺🇸","Paraguay":"🇵🇾","Australia":"🇦🇺","Turkey":"🇹🇷","Germany":"🇩🇪","Curaçao":"🇨🇼","Ivory Coast":"🇨🇮","Ecuador":"🇪🇨","Netherlands":"🇳🇱","Japan":"🇯🇵","Sweden":"🇸🇪","Tunisia":"🇹🇳","Belgium":"🇧🇪","Egypt":"🇪🇬","Iran":"🇮🇷","New Zealand":"🇳🇿","Spain":"🇪🇸","Cape Verde":"🇨🇻","Saudi Arabia":"🇸🇦","Uruguay":"🇺🇾","France":"🇫🇷","Senegal":"🇸🇳","Norway":"🇳🇴","Iraq":"🇮🇶","Argentina":"🇦🇷","Algeria":"🇩🇿","Austria":"🇦🇹","Jordan":"🇯🇴","Portugal":"🇵🇹","DR Congo":"🇨🇩","Uzbekistan":"🇺🇿","Colombia":"🇨🇴","England":"🏴󠁧󠁢󠁥󠁮󠁧󠁿","Croatia":"🇭🇷","Ghana":"🇬🇭","Panama":"🇵🇦"};
const fl=t=>FLAG[t]||"🏳️";
const tf=t=>`${fl(t)} ${t}`;
const short=t=>t.split(" ").pop();

const LOCK_TIME=new Date("2026-06-11T13:00:00Z");
const ADMIN_PIN="2026";
const SK="footiefriend_v4";

// ─── FIFA R32 BRACKET COMBINATIONS ───────────────────────────────────────────
// 16 fixed R32 matches. The 8 slots for 3rd-place teams are determined by
// which 8 groups' 3rd-place teams qualify.
// R32 fixed structure (match number -> description)
// slots: [vs1A=M79, vs1B=M85, vs1D=M81, vs1E=M74, vs1G=M82, vs1I=M77, vs1K=M87, vs1L=M80]

// Map every team to its group letter
const TEAM_TO_GROUP = {};
Object.entries(GROUPS).forEach(([g,teams])=>teams.forEach(t=>{ TEAM_TO_GROUP[t]=g; }));

// FIFA official 495-combination table
// Key = 8 sorted group letters whose 3rd-place teams advance
// Value = [grp vs 1A, grp vs 1B, grp vs 1D, grp vs 1E, grp vs 1G, grp vs 1I, grp vs 1K, grp vs 1L]
const FIFA_TABLE={"EFGHIJKL":["E","J","I","F","H","G","L","K"],"DFGHIJKL":["H","G","I","D","J","F","L","K"],"DEGHIJKL":["E","J","I","D","H","G","L","K"],"DEFHIJKL":["E","J","I","D","H","F","L","K"],"DEFGIJKL":["E","G","I","D","J","F","L","K"],"DEFGHJKL":["E","G","J","D","H","F","L","K"],"DEFGHIKL":["E","G","I","D","H","F","L","K"],"DEFGHIJL":["E","G","J","D","H","F","L","I"],"DEFGHIJK":["E","G","J","D","H","F","I","K"],"CFGHIJKL":["H","G","I","C","J","F","L","K"],"CEGHIJKL":["E","J","I","C","H","G","L","K"],"CEFHIJKL":["E","J","I","C","H","F","L","K"],"CEFGIJKL":["E","G","I","C","J","F","L","K"],"CEFGHJKL":["E","G","J","C","H","F","L","K"],"CEFGHIKL":["E","G","I","C","H","F","L","K"],"CEFGHIJL":["E","G","J","C","H","F","L","I"],"CEFGHIJK":["E","G","J","C","H","F","I","K"],"CDGHIJKL":["H","G","I","C","J","D","L","K"],"CDFHIJKL":["C","J","I","D","H","F","L","K"],"CDFGIJKL":["C","G","I","D","J","F","L","K"],"CDFGHJKL":["C","G","J","D","H","F","L","K"],"CDFGHIKL":["C","G","I","D","H","F","L","K"],"CDFGHIJL":["C","G","J","D","H","F","L","I"],"CDFGHIJK":["C","G","J","D","H","F","I","K"],"CDEHIJKL":["E","J","I","C","H","D","L","K"],"CDEGIJKL":["E","G","I","C","J","D","L","K"],"CDEGHJKL":["E","G","J","C","H","D","L","K"],"CDEGHIKL":["E","G","I","C","H","D","L","K"],"CDEGHIJL":["E","G","J","C","H","D","L","I"],"CDEGHIJK":["E","G","J","C","H","D","I","K"],"CDEFIJKL":["C","J","E","D","I","F","L","K"],"CDEFHJKL":["C","J","E","D","H","F","L","K"],"CDEFHIKL":["C","E","I","D","H","F","L","K"],"CDEFHIJL":["C","J","E","D","H","F","L","I"],"CDEFHIJK":["C","J","E","D","H","F","I","K"],"CDEFGJKL":["C","G","E","D","J","F","L","K"],"CDEFGIKL":["C","G","E","D","I","F","L","K"],"CDEFGIJL":["C","G","E","D","J","F","L","I"],"CDEFGIJK":["C","G","E","D","J","F","I","K"],"CDEFGHKL":["C","G","E","D","H","F","L","K"],"CDEFGHJL":["C","G","J","D","H","F","L","E"],"CDEFGHJK":["C","G","J","D","H","F","E","K"],"CDEFGHIL":["C","G","E","D","H","F","L","I"],"CDEFGHIK":["C","G","E","D","H","F","I","K"],"CDEFGHIJ":["C","G","J","D","H","F","E","I"],"BFGHIJKL":["H","J","B","F","I","G","L","K"],"BEGHIJKL":["E","J","I","B","H","G","L","K"],"BEFHIJKL":["E","J","B","F","I","H","L","K"],"BEFGIJKL":["E","J","B","F","I","G","L","K"],"BEFGHJKL":["E","J","B","F","H","G","L","K"],"BEFGHIKL":["E","G","B","F","I","H","L","K"],"BEFGHIJL":["E","J","B","F","H","G","L","I"],"BEFGHIJK":["E","J","B","F","H","G","I","K"],"BDGHIJKL":["H","J","B","D","I","G","L","K"],"BDFHIJKL":["H","J","B","D","I","F","L","K"],"BDFGIJKL":["I","G","B","D","J","F","L","K"],"BDFGHJKL":["H","G","B","D","J","F","L","K"],"BDFGHIKL":["H","G","B","D","I","F","L","K"],"BDFGHIJL":["H","G","B","D","J","F","L","I"],"BDFGHIJK":["H","G","B","D","J","F","I","K"],"BDEHIJKL":["E","J","B","D","I","H","L","K"],"BDEGIJKL":["E","J","B","D","I","G","L","K"],"BDEGHJKL":["E","J","B","D","H","G","L","K"],"BDEGHIKL":["E","G","B","D","I","H","L","K"],"BDEGHIJL":["E","J","B","D","H","G","L","I"],"BDEGHIJK":["E","J","B","D","H","G","I","K"],"BDEFIJKL":["E","J","B","D","I","F","L","K"],"BDEFHJKL":["E","J","B","D","H","F","L","K"],"BDEFHIKL":["E","I","B","D","H","F","L","K"],"BDEFHIJL":["E","J","B","D","H","F","L","I"],"BDEFHIJK":["E","J","B","D","H","F","I","K"],"BDEFGJKL":["E","G","B","D","J","F","L","K"],"BDEFGIKL":["E","G","B","D","I","F","L","K"],"BDEFGIJL":["E","G","B","D","J","F","L","I"],"BDEFGIJK":["E","G","B","D","J","F","I","K"],"BDEFGHKL":["E","G","B","D","H","F","L","K"],"BDEFGHJL":["H","G","B","D","J","F","L","E"],"BDEFGHJK":["H","G","B","D","J","F","E","K"],"BDEFGHIL":["E","G","B","D","H","F","L","I"],"BDEFGHIK":["E","G","B","D","H","F","I","K"],"BDEFGHIJ":["H","G","B","D","J","F","E","I"],"BCGHIJKL":["H","J","B","C","I","G","L","K"],"BCFHIJKL":["H","J","B","C","I","F","L","K"],"BCFGIJKL":["I","G","B","C","J","F","L","K"],"BCFGHJKL":["H","G","B","C","J","F","L","K"],"BCFGHIKL":["H","G","B","C","I","F","L","K"],"BCFGHIJL":["H","G","B","C","J","F","L","I"],"BCFGHIJK":["H","G","B","C","J","F","I","K"],"BCEHIJKL":["E","J","B","C","I","H","L","K"],"BCEGIJKL":["E","J","B","C","I","G","L","K"],"BCEGHJKL":["E","J","B","C","H","G","L","K"],"BCEGHIKL":["E","G","B","C","I","H","L","K"],"BCEGHIJL":["E","J","B","C","H","G","L","I"],"BCEGHIJK":["E","J","B","C","H","G","I","K"],"BCEFIJKL":["E","J","B","C","I","F","L","K"],"BCEFHJKL":["E","J","B","C","H","F","L","K"],"BCEFHIKL":["E","I","B","C","H","F","L","K"],"BCEFHIJL":["E","J","B","C","H","F","L","I"],"BCEFHIJK":["E","J","B","C","H","F","I","K"],"BCEFGJKL":["E","G","B","C","J","F","L","K"],"BCEFGIKL":["E","G","B","C","I","F","L","K"],"BCEFGIJL":["E","G","B","C","J","F","L","I"],"BCEFGIJK":["E","G","B","C","J","F","I","K"],"BCEFGHKL":["E","G","B","C","H","F","L","K"],"BCEFGHJL":["H","G","B","C","J","F","L","E"],"BCEFGHJK":["H","G","B","C","J","F","E","K"],"BCEFGHIL":["E","G","B","C","H","F","L","I"],"BCEFGHIK":["E","G","B","C","H","F","I","K"],"BCEFGHIJ":["H","G","B","C","J","F","E","I"],"BCDHIJKL":["H","J","B","C","I","D","L","K"],"BCDGIJKL":["I","G","B","C","J","D","L","K"],"BCDGHJKL":["H","G","B","C","J","D","L","K"],"BCDGHIKL":["H","G","B","C","I","D","L","K"],"BCDGHIJL":["H","G","B","C","J","D","L","I"],"BCDGHIJK":["H","G","B","C","J","D","I","K"],"BCDFIJKL":["C","J","B","D","I","F","L","K"],"BCDFHJKL":["C","J","B","D","H","F","L","K"],"BCDFHIKL":["C","I","B","D","H","F","L","K"],"BCDFHIJL":["C","J","B","D","H","F","L","I"],"BCDFHIJK":["C","J","B","D","H","F","I","K"],"BCDFGJKL":["C","G","B","D","J","F","L","K"],"BCDFGIKL":["C","G","B","D","I","F","L","K"],"BCDFGIJL":["C","G","B","D","J","F","L","I"],"BCDFGIJK":["C","G","B","D","J","F","I","K"],"BCDFGHKL":["C","G","B","D","H","F","L","K"],"BCDFGHJL":["H","G","B","D","J","F","L","C"],"BCDFGHJK":["H","G","B","D","J","F","C","K"],"BCDFGHIL":["C","G","B","D","H","F","L","I"],"BCDFGHIK":["C","G","B","D","H","F","I","K"],"BCDFGHIJ":["H","G","B","D","J","F","C","I"],"BCDEIJKL":["E","J","B","C","I","D","L","K"],"BCDEHJKL":["E","J","B","C","H","D","L","K"],"BCDEHIKL":["E","I","B","C","H","D","L","K"],"BCDEHIJL":["E","J","B","C","H","D","L","I"],"BCDEHIJK":["E","J","B","C","H","D","I","K"],"BCDEGIJL":["E","G","B","C","J","D","L","I"],"BCDEGJKL":["E","G","B","C","J","D","L","K"],"BCDEGIKL":["E","G","B","C","I","D","L","K"],"BCDEGIJK":["E","G","B","C","J","D","I","K"],"BCDEGHKL":["E","G","B","C","H","D","L","K"],"BCDEGHJL":["H","G","B","C","J","D","L","E"],"BCDEGHJK":["H","G","B","C","J","D","E","K"],"BCDEGHIL":["E","G","B","C","H","D","L","I"],"BCDEGHIK":["E","G","B","C","H","D","I","K"],"BCDEGHIJ":["H","G","B","C","J","D","E","I"],"BCDEFHKL":["C","J","B","D","H","E","L","K"],"BCDEFHIL":["C","E","B","D","H","F","L","I"],"BCDEFHIK":["C","E","B","D","H","F","I","K"],"BCDEFHIJ":["C","J","B","D","H","F","E","I"],"BCDEFGJL":["C","G","B","D","J","E","L","I"],"BCDEFGKL":["C","G","B","D","E","F","L","K"],"BCDEFGIK":["C","G","B","D","I","E","K","F"],"BCDEFGIJ":["C","G","B","D","J","E","I","F"],"BCDEFGHL":["C","G","B","D","H","E","L","F"],"BCDEFGHK":["C","G","B","D","H","E","K","F"],"BCDEFGHI":["C","G","B","D","H","E","I","F"],"BCDEFIJL":["C","J","B","D","I","E","L","F"],"BCDEFIJK":["C","J","B","D","I","E","K","F"],"BCDEFIKL":["C","E","B","D","I","F","L","K"]};

function getThirdSlots(groupLetters) {
  const key=[...groupLetters].sort().join("");
  return FIFA_TABLE[key]||null;
}

function buildR32(groupRankings, thirdPlace) {
  // Get 1st and 2nd place from each group
  const get = (g, pos) => (groupRankings[g] || [])[pos] || `${pos===0?"1st":"2nd"} Group ${g}`;

  // Convert thirdPlace team names -> group letters for lookup
  const thirdGroups = thirdPlace
    .map(team => {
      // Find which group this team is ranked 3rd in according to user's rankings
      for (const [g, ranked] of Object.entries(groupRankings)) {
        if (ranked[2] === team) return g;
      }
      // Fallback: use team's actual group
      return TEAM_TO_GROUP[team];
    })
    .filter(Boolean);

  // Fixed matches
  const fixed = [
    {id:"M73", home: get("A",1), away: get("B",1), label:"2A vs 2B"},
    {id:"M75", home: get("F",0), away: get("C",1), label:"1F vs 2C"},
    {id:"M76", home: get("C",0), away: get("F",1), label:"1C vs 2F"},
    {id:"M78", home: get("E",1), away: get("I",1), label:"2E vs 2I"},
    {id:"M83", home: get("K",1), away: get("L",1), label:"2K vs 2L"},
    {id:"M84", home: get("H",0), away: get("J",1), label:"1H vs 2J"},
    {id:"M86", home: get("J",0), away: get("H",1), label:"1J vs 2H"},
    {id:"M88", home: get("D",1), away: get("G",1), label:"2D vs 2G"},
  ];
  // Third-place dependent matches
  // Try FIFA table lookup first; if not found, distribute thirds in group order
  const slots = getThirdSlots(thirdGroups);
  const getThird = (slotIdx) => {
    if (slots && slots[slotIdx]) {
      const g = slots[slotIdx];
      return (groupRankings[g]||[])[2] || `3rd Group ${g}`;
    }
    // Fallback: just use the team directly from thirdPlace by index
    if (thirdPlace[slotIdx]) return thirdPlace[slotIdx];
    return "Best 3rd";
  };
  const thirdMatches = [
    {id:"M74", home: get("E",0), away: getThird(3), label:"1E vs Best 3rd"},
    {id:"M77", home: get("I",0), away: getThird(5), label:"1I vs Best 3rd"},
    {id:"M79", home: get("A",0), away: getThird(0), label:"1A vs Best 3rd"},
    {id:"M80", home: get("L",0), away: getThird(7), label:"1L vs Best 3rd"},
    {id:"M81", home: get("D",0), away: getThird(2), label:"1D vs Best 3rd"},
    {id:"M82", home: get("G",0), away: getThird(4), label:"1G vs Best 3rd"},
    {id:"M85", home: get("B",0), away: getThird(1), label:"1B vs Best 3rd"},
    {id:"M87", home: get("K",0), away: getThird(6), label:"1K vs Best 3rd"},
  ];
  // All 16 R32 matches in order
  const all = [...fixed, ...thirdMatches];
  all.sort((a,b)=>parseInt(a.id.slice(1))-parseInt(b.id.slice(1)));
  return all;
}

// ─── COLORS & STYLES ─────────────────────────────────────────────────────────
const C={bg:"#0a0e1a",card:"#111827",border:"#1f2937",accent:"#22c55e",aD:"#14532d",gold:"#f59e0b",gD:"#78350f",red:"#ef4444",rD:"#7f1d1d",text:"#f9fafb",muted:"#6b7280",inp:"#1f2937"};
const btn=(v="p",mt=8)=>({background:v==="p"?C.accent:v==="g"?C.gold:v==="r"?C.red:C.inp,color:v==="g"?"#000":C.text,border:"none",borderRadius:8,padding:"9px 16px",fontWeight:700,fontSize:13,cursor:"pointer",width:"100%",marginTop:mt});
const inp={background:C.inp,border:`1px solid ${C.border}`,borderRadius:8,color:C.text,padding:"9px 11px",fontSize:13,width:"100%",boxSizing:"border-box",marginTop:5,outline:"none"};
const card={background:C.card,border:`1px solid ${C.border}`,borderRadius:12,padding:14,marginBottom:10};

const ld=()=>{try{const r=localStorage.getItem(SK);return r?JSON.parse(r):null;}catch{return null;}};
const sv=s=>{try{localStorage.setItem(SK,JSON.stringify(s));}catch{}};
const dA=()=>({users:[],lobbies:[],results:{matches:{},groupRankings:{},advancingThirds:[],knockout:{R32:[],R16:[],QF:[],SF:[],Final:[],Winner:null},goals:{},knockoutRounds:{},topScorer:"",mvp:"",topScorerAccepted:[],mvpAccepted:[]}});
const gc=()=>Math.random().toString(36).substring(2,7).toUpperCase();

// ─── SCORING ──────────────────────────────────────────────────────────────────
function scoreUser(user,res){
  const t=user.tips||{};
  let gM=0,gR=0,t3=0,r32=0,r16=0,qf=0,sf=0,fin=0,win=0,sp=0,dass=0;
  ALL_MATCHES.forEach(m=>{const r=res.matches?.[m.id],tip=t.matches?.[m.id];if(!r||tip===undefined||r.home===""||r.away==="")return;const a=r.home>r.away?"1":r.home<r.away?"2":"X";if(tip===a)gM++;});
  Object.keys(GROUPS).forEach(g=>{const a=res.groupRankings?.[g]||[],tp=t.groupRankings?.[g]||[];tp.forEach((x,i)=>{if(a[i]===x)gR++;});});
  (t.thirdPlace||[]).forEach(x=>{if((res.advancingThirds||[]).includes(x))t3++;});
  const rm={R32:3,R16:3,QF:3,SF:10,Final:15};
  ["R32","R16","QF","SF","Final"].forEach(rd=>{const a=res.knockout?.[rd]||[],tp=t.knockout?.[rd]||[],p=rm[rd];tp.forEach(x=>{if(a.includes(x)){if(rd==="R32")r32+=p;else if(rd==="R16")r16+=p;else if(rd==="QF")qf+=p;else if(rd==="SF")sf+=p;else if(rd==="Final")fin+=p;}});});
  const norm=s=>s.trim().toLowerCase().normalize("NFD").replace(/[\u0300-\u036f]/g,"").replace(/[^a-z0-9]/g,"");
  if(t.topScorer&&(res.topScorerAccepted||[]).includes(norm(t.topScorer)))sp+=10;
  if(t.mvp&&(res.mvpAccepted||[]).includes(norm(t.mvp)))sp+=10;
  const dt=t.dass;
  if(dt){let g=res.goals?.[dt]||0,gp=0;ALL_MATCHES.forEach(m=>{const r=res.matches?.[m.id];if(!r||r.home===""||r.away==="")return;if(m.home===dt)gp+=r.home>r.away?3:r.home===r.away?1:0;if(m.away===dt)gp+=r.away>r.home?3:r.away===r.home?1:0;});dass=-(g+gp+(res.knockoutRounds?.[dt]||0)*2);}
  const gT=gM+gR+t3;
  return{gM,gR,t3,gT,r32,r16,qf,sf,fin,win,sp,dass,total:gT+r32+r16+qf+sf+fin+win+sp+dass};
}

// ─── BRACKET COMPONENT ────────────────────────────────────────────────────────
function MatchCard({home, away, winner, onPick, locked, matchId, pts}) {
  const homeSel = winner === home;
  const awaySel = winner === away;
  const isPlaceholder = !home || !away || home.startsWith("Winner") || home.startsWith("1st") || home.startsWith("2nd") || home.startsWith("Best") || away.startsWith("Winner") || away.startsWith("1st") || away.startsWith("2nd") || away.startsWith("Best");

  return (
    <div style={{...card, padding:"8px 10px", marginBottom:6}}>
      {pts && <div style={{fontSize:9,color:C.gold,fontWeight:800,letterSpacing:1,marginBottom:4}}>+{pts}pts each</div>}
      {[home,away].map((team,i)=>{
        const sel = i===0 ? homeSel : awaySel;
        const isPlaceholderTeam = !team || team.startsWith("Winner") || team.startsWith("1st") || team.startsWith("2nd") || team.startsWith("Best") || team.startsWith("3rd");
        return (
          <button key={i} disabled={locked||isPlaceholder||isPlaceholderTeam} onClick={()=>onPick&&onPick(team)} style={{
            display:"flex", alignItems:"center", gap:8, width:"100%",
            padding:"7px 8px", marginBottom:i===0?3:0, borderRadius:8,
            border:`1px solid ${sel?C.accent:C.border}`,
            background:sel?C.aD:isPlaceholderTeam?"#0c1117":C.inp,
            color:sel?C.text:isPlaceholderTeam?C.muted:C.text,
            cursor:locked||isPlaceholderTeam?"default":"pointer",
            fontWeight:sel?700:400, fontSize:12, textAlign:"left",
          }}>
            <span style={{fontSize:15}}>{isPlaceholderTeam?"🔲":fl(team)}</span>
            <span style={{flex:1}}>{isPlaceholderTeam?(team||"TBD"):team}</span>
            {sel&&<span style={{color:C.accent,fontSize:12}}>✓</span>}
          </button>
        );
      })}
    </div>
  );
}

function BracketView({groupRankings, thirdPlace, ko, onPickKO, locked}) {
  const r32Matches = buildR32(groupRankings, thirdPlace);

  // Build R16 pairs from R32 winners
  // Official pairing: winners of adjacent R32 matches face each other
  // M73w vs M74w, M75w vs M76w, M77w vs M78w, M79w vs M80w,
  // M81w vs M82w, M83w vs M84w, M85w vs M86w, M87w vs M88w
  const r32Winners = ko.R32||[];
  const r32Map = {};
  r32Matches.forEach(m=>{if(r32Winners.includes(m.home))r32Map[m.id]=m.home;else if(r32Winners.includes(m.away))r32Map[m.id]=m.away;});

  const R16_PAIRS = [
    ["M73","M74"],["M75","M76"],["M77","M78"],["M79","M80"],
    ["M81","M82"],["M83","M84"],["M85","M86"],["M87","M88"],
  ];
  const r16Matches = R16_PAIRS.map((pair,i)=>({
    id:`R16_${i}`,
    home: r32Map[pair[0]] || `Winner ${pair[0]}`,
    away: r32Map[pair[1]] || `Winner ${pair[1]}`,
  }));

  const r16Winners = ko.R16||[];
  const r16Map = {};
  r16Matches.forEach(m=>{if(r16Winners.includes(m.home))r16Map[m.id]=m.home;else if(r16Winners.includes(m.away))r16Map[m.id]=m.away;});

  const QF_PAIRS = [["R16_0","R16_1"],["R16_2","R16_3"],["R16_4","R16_5"],["R16_6","R16_7"]];
  const qfMatches = QF_PAIRS.map((pair,i)=>({
    id:`QF_${i}`,
    home: r16Map[pair[0]] || `Winner ${pair[0]}`,
    away: r16Map[pair[1]] || `Winner ${pair[1]}`,
  }));

  const qfWinners = ko.QF||[];
  const qfMap = {};
  qfMatches.forEach(m=>{if(qfWinners.includes(m.home))qfMap[m.id]=m.home;else if(qfWinners.includes(m.away))qfMap[m.id]=m.away;});

  const SF_PAIRS = [["QF_0","QF_1"],["QF_2","QF_3"]];
  const sfMatches = SF_PAIRS.map((pair,i)=>({
    id:`SF_${i}`,
    home: qfMap[pair[0]] || `Winner ${pair[0]}`,
    away: qfMap[pair[1]] || `Winner ${pair[1]}`,
  }));

  const sfWinners = ko.SF||[];
  const sfMap = {};
  sfMatches.forEach(m=>{if(sfWinners.includes(m.home))sfMap[m.id]=m.home;else if(sfWinners.includes(m.away))sfMap[m.id]=m.away;});

  const finalMatch = {
    id:"Final",
    home: sfMap["SF_0"] || "Winner SF1",
    away: sfMap["SF_1"] || "Winner SF2",
  };

  const pickKO = (round, team, matchPool, max) => {
    if (!team || team.startsWith("Winner") || team.startsWith("Best")) return;
    onPickKO(round, team, matchPool, max);
  };

  const rounds = [
    {id:"R32", label:"Round of 32", pts:3, matches:r32Matches, cur:ko.R32||[], max:16},
    {id:"R16", label:"Round of 16", pts:3, matches:r16Matches, cur:ko.R16||[], max:8},
    {id:"QF",  label:"Quarter Finals", pts:3, matches:qfMatches, cur:ko.QF||[], max:4},
    {id:"SF",  label:"Semi Finals", pts:10, matches:sfMatches, cur:ko.SF||[], max:2},
    {id:"Final",label:"🏆 Final – Pick the Winner", pts:15, matches:[finalMatch], cur:ko.Final||[], max:1},
  ];

  return (
    <div style={{padding:"8px 6px", maxWidth:520, margin:"0 auto"}}>
      <div style={{fontSize:12,color:C.muted,marginBottom:12,lineHeight:1.6}}>
        Tap the team you think wins each match. Each round auto-populates from your previous picks.
        {!thirdPlace||thirdPlace.length<8?<span style={{color:C.gold}}> ⚠️ Complete thirds tab first for accurate R32 matchups.</span>:null}
      </div>

      {rounds.map(round=>(
        <div key={round.id}>
          <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",margin:"16px 0 8px"}}>
            <div style={{fontWeight:900,fontSize:14,color:C.accent}}>{round.label}</div>
            <div style={{fontSize:11,color:C.muted}}>{round.cur.length}/{round.max} picked · <span style={{color:C.gold}}>{round.pts}pts</span></div>
          </div>
          {round.matches.map(m=>(
            <MatchCard
              key={m.id}
              home={m.home} away={m.away}
              winner={round.cur.includes(m.home)?m.home:round.cur.includes(m.away)?m.away:null}
              onPick={(team)=>pickKO(round.id, team, round.matches, round.max)}
              locked={locked}
              matchId={m.id}
            />
          ))}
        </div>
      ))}


    </div>
  );
}

// ─── AUTH ─────────────────────────────────────────────────────────────────────
function Auth({onLogin,onAdmin}){
  const [mode,setMode]=useState("login");
  const [name,setName]=useState("");const [pin,setPin]=useState("");const [err,setErr]=useState("");
  const go=()=>{
    if(mode==="admin"){if(pin===ADMIN_PIN)onAdmin();else setErr("Wrong admin PIN.");return;}
    if(!name.trim()){setErr("Enter your name.");return;}
    if(pin.length<4){setErr("PIN must be 4–6 digits.");return;}
    onLogin(name.trim(),pin,mode==="register");
  };
  return(
    <div style={{padding:16,maxWidth:380,margin:"0 auto"}}>
      <div style={{...card,marginTop:24,textAlign:"center"}}>
        <div style={{fontSize:48,marginBottom:4}}>⚽</div>
        <div style={{fontSize:22,fontWeight:900}}>FootieFriend</div>
        <div style={{fontSize:11,color:C.muted,letterSpacing:3,marginBottom:20}}>WORLD CUP 2026</div>
        <div style={{display:"flex",gap:5,marginBottom:18}}>
          {["login","register","admin"].map(m=>(
            <button key={m} onClick={()=>{setMode(m);setErr("");setPin("");}} style={{...btn(mode===m?"p":"s",0),flex:1,fontSize:11,padding:"8px 4px"}}>
              {m==="login"?"Log In":m==="register"?"Sign Up":"🔧 Admin"}
            </button>
          ))}
        </div>
        {mode!=="admin"&&<><div style={{fontSize:11,color:C.muted,fontWeight:600,textTransform:"uppercase"}}>Name</div><input style={inp} placeholder="Your name" value={name} onChange={e=>setName(e.target.value)} onKeyDown={e=>e.key==="Enter"&&go()}/></>}
        <div style={{fontSize:11,color:C.muted,fontWeight:600,textTransform:"uppercase",marginTop:10}}>{mode==="admin"?"Admin PIN":"PIN (4–6 digits)"}</div>
        <input style={inp} type="password" placeholder="••••" value={pin} onChange={e=>setPin(e.target.value)} maxLength={10} onKeyDown={e=>e.key==="Enter"&&go()}/>
        {err&&<div style={{color:C.red,fontSize:12,marginTop:6}}>{err}</div>}
        <button style={btn("p")} onClick={go}>{mode==="login"?"Log In":mode==="register"?"Create Account":"Enter Admin"}</button>
      </div>
    </div>
  );
}

// ─── LOBBIES ──────────────────────────────────────────────────────────────────
function Lobbies({user,lobbies,onJoin,onCreate,onEnter,onLogout}){
  const [code,setCode]=useState("");const [nm,setNm]=useState("");const [err,setErr]=useState("");
  const mine=lobbies.filter(l=>user.groups?.includes(l.code));
  return(
    <div style={{padding:16,maxWidth:460,margin:"0 auto"}}>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:16}}>
        <div><div style={{fontWeight:800,fontSize:16}}>👋 {user.name}</div><div style={{fontSize:11,color:C.muted}}>Your groups</div></div>
        <button onClick={onLogout} style={{...btn("s",0),width:"auto",padding:"6px 12px",fontSize:11}}>Log out</button>
      </div>
      {mine.length===0&&<div style={{...card,textAlign:"center",color:C.muted,padding:28,fontSize:13}}>Join or create a group to get started! 🏆</div>}
      {mine.map(l=>(
        <div key={l.code} style={{...card,cursor:"pointer",display:"flex",justifyContent:"space-between",alignItems:"center"}} onClick={()=>onEnter(l.code)}>
          <div><div style={{fontWeight:800,fontSize:14}}>{l.name}</div><div style={{fontSize:11,color:C.muted,marginTop:2}}>Code: <span style={{color:C.accent,fontWeight:700,letterSpacing:1}}>{l.code}</span></div></div>
          <div style={{color:C.muted,fontSize:22}}>›</div>
        </div>
      ))}
      <div style={{...card,marginTop:16}}>
        <div style={{fontSize:15,fontWeight:800,marginBottom:8,color:C.accent}}>Join a Group</div>
        <input style={inp} placeholder="5-letter code" value={code} onChange={e=>setCode(e.target.value.toUpperCase())} maxLength={5}/>
        {err&&<div style={{color:C.red,fontSize:12,marginTop:5}}>{err}</div>}
        <button style={btn("p")} onClick={()=>{const l=lobbies.find(x=>x.code===code);if(!l){setErr("Not found.");return;}if(user.groups?.includes(code)){setErr("Already a member.");return;}onJoin(code);setCode("");setErr("");}}>Join Group</button>
      </div>
      <div style={card}>
        <div style={{fontSize:15,fontWeight:800,marginBottom:8,color:C.accent}}>Create a Group</div>
        <input style={inp} placeholder="e.g. Office 2026" value={nm} onChange={e=>setNm(e.target.value)}/>
        <button style={btn("g")} onClick={()=>{if(!nm.trim())return;onCreate(nm.trim());setNm("");}}>Create Group</button>
      </div>
    </div>
  );
}

// ─── TIPS FORM ────────────────────────────────────────────────────────────────
function TipsForm({user,locked,onSave}){
  const init=user.tips||{};
  const [tab,setTab]=useState("matches");
  const [matches,setMatches]=useState(init.matches||{});
  const [gRank,setGRank]=useState(init.groupRankings||{});
  const [thirds,setThirds]=useState(init.thirdPlace||[]);
  const [ko,setKo]=useState(init.knockout||{R32:[],R16:[],QF:[],SF:[],Final:[]});
  const [winner,setWinner]=useState(init.winner||"");
  const [dass,setDass]=useState(init.dass||"");
  const [topScorer,setTopScorer]=useState(init.topScorer||"");
  const [mvp,setMvp]=useState(init.mvp||"");
  const [saved,setSaved]=useState(false);

  const allThirds=Object.keys(GROUPS).map(g=>({g,team:(gRank[g]||[])[2]})).filter(x=>x.team);
  const toggleRank=(g,team)=>setGRank(r=>{const c=[...(r[g]||[])];const i=c.indexOf(team);if(i>=0)c.splice(i,1);else if(c.length<4)c.push(team);return{...r,[g]:c};});
  const toggleThird=t=>setThirds(x=>x.includes(t)?x.filter(v=>v!==t):x.length<8?[...x,t]:x);

  const pickKO=(round, team, matchList, max)=>{
    setKo(k=>{
      const cur=k[round]||[];
      // Find which match this team is in and remove the other team from that match
      const match = matchList.find(m=>m.home===team||m.away===team);
      const opponent = match ? (match.home===team?match.away:match.home) : null;
      let newCur;
      if(cur.includes(team)){
        newCur=cur.filter(x=>x!==team);
      } else {
        // Remove opponent if they were picked, then add this team
        newCur=[...cur.filter(x=>x!==opponent),team];
        if(newCur.length>max) newCur=newCur.slice(-max);
      }
      const nk={...k,[round]:newCur};
      // Cascade: remove this team from later rounds if deselecting
      if(!newCur.includes(team)&&cur.includes(team)){
        if(round==="R32"||round==="R16"||round==="QF"||round==="SF"){
          nk.R16=(k.R16||[]).filter(x=>x!==team&&x!==opponent);
          nk.QF=(k.QF||[]).filter(x=>x!==team&&x!==opponent);
          nk.SF=(k.SF||[]).filter(x=>x!==team&&x!==opponent);
          nk.Final=(k.Final||[]).filter(x=>x!==team&&x!==opponent);
          if(winner===team||winner===opponent)setWinner("");
        }
      }
      return nk;
    });
  };

  const tabs=[{id:"matches",icon:"⚽"},{id:"groups",icon:"📊"},{id:"thirds",icon:"3️⃣"},{id:"bracket",icon:"🏟️"},{id:"special",icon:"⭐"},{id:"dass",icon:"💩"}];
  const labels={matches:"Match Predictions",groups:"Group Rankings",thirds:"Third Place",bracket:"Knockout Bracket",special:"Specials",dass:"Dass-Loppa"};

  return(
    <div style={{padding:"10px 8px",maxWidth:520,margin:"0 auto"}}>
      {locked&&<div style={{background:C.rD,border:`1px solid ${C.red}`,borderRadius:10,padding:10,marginBottom:10,fontSize:12,textAlign:"center",fontWeight:600}}>🔒 Tips locked – tournament has started!</div>}
      <div style={{display:"flex",background:C.card,borderRadius:10,padding:3,marginBottom:4,border:`1px solid ${C.border}`}}>
        {tabs.map(t=><button key={t.id} onClick={()=>setTab(t.id)} style={{flex:1,padding:"7px 2px",background:tab===t.id?C.accent:"transparent",border:"none",borderRadius:8,color:tab===t.id?"#000":C.muted,cursor:"pointer",fontSize:15,fontWeight:700}}>{t.icon}</button>)}
      </div>
      <div style={{fontSize:11,color:C.muted,textAlign:"center",marginBottom:10,fontWeight:600,letterSpacing:1}}>{labels[tab]?.toUpperCase()}</div>

      {tab==="matches"&&(
        <div>
          <div style={{display:"flex",justifyContent:"space-between",fontSize:14,fontWeight:800,color:C.accent,marginBottom:8}}>
            <span>1 / X / 2</span><span style={{fontSize:11,color:C.muted,fontWeight:400}}>{Object.keys(matches).length}/{ALL_MATCHES.length}</span>
          </div>
          {SCHEDULE.map(day=>(
            <div key={day.date}>
              <div style={{fontSize:11,color:C.gold,fontWeight:800,letterSpacing:1,margin:"12px 0 5px"}}>
                <span style={{background:"#1c1505",border:"1px solid #78350f",borderRadius:6,padding:"3px 8px"}}>📅 {day.date}</span>
              </div>
              {day.matches.map(m=>(
                <div key={m.id} style={{...card,marginBottom:6,padding:"8px 10px"}}>
                  <div style={{fontSize:9,color:C.muted,fontWeight:700,marginBottom:5,letterSpacing:1}}>GROUP {m.g}</div>
                  <div style={{display:"flex",alignItems:"center",gap:4}}>
                    <div style={{flex:1,textAlign:"right"}}><div style={{fontSize:18}}>{fl(m.home)}</div><div style={{fontSize:10,color:C.muted}}>{m.home}</div></div>
                    <div style={{display:"flex",gap:3}}>
                      {["1","X","2"].map(v=>(
                        <button key={v} disabled={locked} onClick={()=>setMatches(ms=>({...ms,[m.id]:v}))} style={{width:33,height:33,borderRadius:7,border:"none",cursor:locked?"default":"pointer",fontWeight:700,fontSize:12,background:matches[m.id]===v?(v==="X"?C.gold:C.accent):C.inp,color:matches[m.id]===v&&v==="X"?"#000":C.text,transform:matches[m.id]===v?"scale(1.1)":"scale(1)"}}>{v}</button>
                      ))}
                    </div>
                    <div style={{flex:1,textAlign:"left"}}><div style={{fontSize:18}}>{fl(m.away)}</div><div style={{fontSize:10,color:C.muted}}>{m.away}</div></div>
                  </div>
                </div>
              ))}
            </div>
          ))}
        </div>
      )}

      {tab==="groups"&&(
        <div>
          <div style={{fontSize:12,color:C.muted,marginBottom:12}}>Tap teams in order 1st→4th. <b style={{color:C.gold}}>1pt per correct position.</b></div>
          {Object.entries(GROUPS).map(([g,teams])=>{
            const ranked=gRank[g]||[];
            const pC=["#14532d","#1e3a5f","#431407","#1a1a2e"];
            const pB=[C.accent,"#3b82f6","#f97316","#6b7280"];
            const pL=["1st 🥇","2nd 🥈","3rd","4th"];
            return(
              <div key={g} style={card}>
                <div style={{fontWeight:800,fontSize:12,color:C.accent,marginBottom:8}}>GROUP {g}</div>
                <div style={{display:"flex",gap:3,marginBottom:8}}>
                  {[0,1,2,3].map(i=>(
                    <div key={i} style={{flex:1,background:ranked[i]?pC[i]:C.inp,border:`1px solid ${ranked[i]?pB[i]:C.border}`,borderRadius:8,padding:"4px 2px",textAlign:"center",minHeight:48,display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center"}}>
                      <div style={{fontSize:9,color:C.muted,fontWeight:700}}>{pL[i]}</div>
                      {ranked[i]&&<><div style={{fontSize:18,marginTop:2}}>{fl(ranked[i])}</div><div style={{fontSize:8,color:C.text,marginTop:1}}>{short(ranked[i])}</div></>}
                    </div>
                  ))}
                </div>
                <div style={{display:"flex",flexWrap:"wrap",gap:4}}>
                  {teams.map(t=>{const pos=ranked.indexOf(t);const sel=pos>=0;return(
                    <button key={t} disabled={locked} onClick={()=>toggleRank(g,t)} style={{padding:"5px 8px",borderRadius:7,cursor:locked?"default":"pointer",border:`1px solid ${sel?pB[pos]:C.border}`,background:sel?pC[pos]:C.inp,color:C.text,fontSize:11,fontWeight:sel?700:400,display:"flex",alignItems:"center",gap:3}}>
                      {fl(t)} {short(t)} {sel&&<span style={{color:C.gold,fontSize:9,fontWeight:800}}>{pos+1}</span>}
                    </button>
                  );})}
                </div>
              </div>
            );
          })}
        </div>
      )}

      {tab==="thirds"&&(
        <div>
          <div style={{fontSize:12,color:C.muted,marginBottom:10}}>Pick <b style={{color:C.accent}}>8 of 12</b> third-placed teams you think advance. <b style={{color:C.gold}}>1pt each.</b> They'll appear in the correct bracket slots!</div>
          {allThirds.length<12&&<div style={{...card,textAlign:"center",color:C.gold,fontSize:12}}>⚠️ Rank all 12 groups first!<br/><span style={{color:C.muted,fontSize:11}}>{allThirds.length}/12 ranked</span></div>}
          {allThirds.length>0&&<div style={card}>
            <div style={{fontSize:11,color:C.muted,marginBottom:8,textAlign:"right"}}>{thirds.length}/8 selected</div>
            {allThirds.map(({g,team})=>{
              const sel=thirds.includes(team),full=!sel&&thirds.length>=8;
              return(
                <button key={g} disabled={locked||full} onClick={()=>toggleThird(team)} style={{display:"flex",alignItems:"center",gap:8,width:"100%",padding:"9px 10px",marginBottom:4,borderRadius:9,cursor:locked||full?"default":"pointer",background:sel?C.aD:full?"#0f172a":C.inp,border:`1px solid ${sel?C.accent:C.border}`,color:full?C.muted:C.text,fontWeight:sel?700:400,opacity:full?0.5:1}}>
                  <span style={{fontSize:10,color:C.muted,width:18,fontWeight:700}}>G{g}</span>
                  <span style={{fontSize:16}}>{fl(team)}</span>
                  <span style={{flex:1,fontSize:13}}>{team}</span>
                  {sel&&<span style={{color:C.accent,fontWeight:700}}>✓</span>}
                  {full&&<span style={{fontSize:10}}>full</span>}
                </button>
              );
            })}
          </div>}
        </div>
      )}

      {tab==="bracket"&&(
        <BracketView
          groupRankings={gRank}
          thirdPlace={thirds}
          ko={ko}
          onPickKO={pickKO}
          locked={locked}
        />
      )}

      {tab==="special"&&(
        <div>
          <div style={card}><div style={{fontWeight:700,marginBottom:4}}>⚽ Top Scorer – Golden Boot <span style={{color:C.gold,fontSize:12}}>(10pts)</span></div><div style={{fontSize:12,color:C.muted,marginBottom:6}}>Type the player's name – admin verifies</div><input style={inp} disabled={locked} placeholder="e.g. Kylian Mbappé" value={topScorer} onChange={e=>setTopScorer(e.target.value)}/></div>
          <div style={card}><div style={{fontWeight:700,marginBottom:4}}>🌟 Best Player – Golden Ball <span style={{color:C.gold,fontSize:12}}>(10pts)</span></div><div style={{fontSize:12,color:C.muted,marginBottom:6}}>Type the player's name – admin verifies</div><input style={inp} disabled={locked} placeholder="e.g. Lamine Yamal" value={mvp} onChange={e=>setMvp(e.target.value)}/></div>
        </div>
      )}

      {tab==="dass"&&(
        <div>
          <div style={{...card,border:`1px solid ${C.rD}`,marginBottom:12}}><div style={{fontSize:13,color:C.muted,lineHeight:1.8}}>Pick the team you dread most.<br/><b style={{color:C.red}}>–1pt</b> per goal · <b style={{color:C.red}}>–1pt</b> per group stage point · <b style={{color:C.red}}>–2pts</b> per knockout round</div></div>
          <div style={{display:"flex",flexWrap:"wrap",gap:4}}>
            {ALL_TEAMS.map(t=>{const sel=dass===t;return(<button key={t} disabled={locked} onClick={()=>setDass(sel?"":t)} style={{padding:"6px 9px",borderRadius:8,cursor:locked?"default":"pointer",border:`1px solid ${sel?C.red:C.border}`,background:sel?C.rD:C.inp,color:sel?C.red:C.text,fontWeight:sel?800:400,fontSize:11}}>{fl(t)} {short(t)} {sel&&"💩"}</button>);})}
          </div>
          {dass&&<div style={{marginTop:12,padding:12,background:C.rD,borderRadius:10,textAlign:"center",border:`1px solid ${C.red}`}}><div style={{fontSize:11,color:C.muted}}>Your dass-loppa</div><div style={{fontSize:18,fontWeight:800,color:C.red,marginTop:4}}>💩 {tf(dass)}</div></div>}
        </div>
      )}

      {!locked&&<button style={{...btn("g"),marginTop:14,fontSize:14,padding:"12px 0"}} onClick={()=>{onSave({matches,groupRankings:gRank,thirdPlace:thirds,knockout:ko,dass,topScorer,mvp});setSaved(true);setTimeout(()=>setSaved(false),2000);}}>{saved?"✅ Tips Saved!":"💾 Save My Tips"}</button>}
    </div>
  );
}

// ─── LEADERBOARD ──────────────────────────────────────────────────────────────
function Leaderboard({lobby,users,results}){
  const members=users.filter(u=>u.groups?.includes(lobby.code));
  const scored=members.map(u=>({...u,s:scoreUser(u,results)})).sort((a,b)=>b.s.total-a.s.total);
  const cols=[{k:"total",l:"PTS",c:C.gold,bold:true,big:true},{k:"gT",l:"GRP"},{k:"r32",l:"R32"},{k:"r16",l:"R16"},{k:"qf",l:"QF"},{k:"sf",l:"SF"},{k:"fin",l:"FIN"},{k:"sp",l:"⭐"},{k:"dass",l:"💩",c:C.red}];
  return(
    <div style={{padding:"12px 6px",maxWidth:600,margin:"0 auto"}}>
      <div style={{fontWeight:900,fontSize:18,marginBottom:2}}>{lobby.name}</div>
      <div style={{fontSize:11,color:C.muted,marginBottom:14}}>Code: <span style={{color:C.accent,fontWeight:700,letterSpacing:1}}>{lobby.code}</span> · {members.length} member{members.length!==1?"s":""}</div>
      {members.length===0&&<div style={{...card,textAlign:"center",color:C.muted,padding:32}}>No members yet. Share the code! 📣</div>}
      {members.length>0&&<div style={{overflowX:"auto"}}>
        <table style={{width:"100%",borderCollapse:"collapse",fontSize:11,minWidth:500}}>
          <thead><tr style={{borderBottom:`2px solid ${C.border}`}}>
            <th style={{textAlign:"left",padding:"6px 4px",color:C.muted,width:28}}>#</th>
            <th style={{textAlign:"left",padding:"6px 4px",color:C.muted}}>Player</th>
            {cols.map(c=><th key={c.k} style={{textAlign:"center",padding:"6px 3px",color:c.c||C.muted,fontWeight:700}}>{c.l}</th>)}
          </tr></thead>
          <tbody>{scored.map((u,i)=>(
            <tr key={u.id} style={{borderBottom:`1px solid ${C.border}`,background:i===0?"#0d1f0d":i%2===0?"transparent":"#0c1117"}}>
              <td style={{padding:"8px 4px",fontWeight:700,fontSize:14}}>{i===0?"🥇":i===1?"🥈":i===2?"🥉":<span style={{color:C.muted,fontSize:11}}>{i+1}</span>}</td>
              <td style={{padding:"8px 4px",fontWeight:600,fontSize:12}}>{u.name}</td>
              {cols.map(c=><td key={c.k} style={{textAlign:"center",padding:"8px 3px",fontWeight:c.bold?900:400,color:c.k==="dass"?C.red:c.k==="total"?C.gold:C.text,fontSize:c.big?14:11}}>{u.s[c.k]!==0?u.s[c.k]:<span style={{color:C.border}}>–</span>}</td>)}
            </tr>
          ))}</tbody>
        </table>
      </div>}
    </div>
  );
}

// ─── EXCEL EXPORT ────────────────────────────────────────────────────────────
function buildLeaderboardCSV(appState, results) {
  const users = appState.users || [];
  const rows = [];
  const header = ["Name","Total","Group (1X2)","Group Rank","3rd Place","R32","R16","QF","SF","Final","Winner","Specials","Dass","Top Scorer Tip","MVP Tip","Dass-Loppa",...Object.keys(GROUPS).map(g=>`Group ${g} Ranking`)];
  rows.push(header);
  users.forEach(u => {
    const s = scoreUser(u, results);
    const tips = u.tips || {};
    const grpRankings = Object.keys(GROUPS).map(g => (tips.groupRankings?.[g]||[]).join(" > ") || "-");
    rows.push([u.name,s.total,s.gM,s.gR,s.t3,s.r32,s.r16,s.qf,s.sf,s.fin,s.win,s.sp,s.dass,tips.topScorer||"-",tips.mvp||"-",tips.dass||"-",...grpRankings]);
  });
  return rows.map(r=>r.map(c=>{const s=String(c??"");return s.includes(",")||s.includes('"')?`"${s.replace(/"/g,'""')}"`  :s;}).join(",")).join("\n");
}

function exportToExcel(appState, results, onShow) {
  const csv = buildLeaderboardCSV(appState, results);
  onShow(csv, "footiefriend_leaderboard.csv");
}

// ─── CSV MODAL ────────────────────────────────────────────────────────────────
function CSVModal({csv, filename, onClose}) {
  const [copied, setCopied] = useState(false);
  const copy = () => {
    navigator.clipboard.writeText(csv).then(() => {
      setCopied(true);
      setTimeout(() => setCopied(false), 2000);
    });
  };
  return(
    <div style={{position:"fixed",top:0,left:0,right:0,bottom:0,background:"rgba(0,0,0,0.85)",zIndex:1000,display:"flex",flexDirection:"column",padding:16}}>
      <div style={{background:C.card,borderRadius:12,border:`1px solid ${C.border}`,display:"flex",flexDirection:"column",maxHeight:"90vh",overflow:"hidden"}}>
        <div style={{padding:"12px 14px",borderBottom:`1px solid ${C.border}`,display:"flex",justifyContent:"space-between",alignItems:"center"}}>
          <div>
            <div style={{fontWeight:800,fontSize:14,color:C.accent}}>📊 {filename}</div>
            <div style={{fontSize:11,color:C.muted,marginTop:2}}>Copy the text below and paste into Excel or Google Sheets</div>
          </div>
          <button onClick={onClose} style={{background:"none",border:"none",color:C.muted,fontSize:22,cursor:"pointer",padding:"0 4px"}}>✕</button>
        </div>
        <div style={{flex:1,overflowY:"auto",padding:12}}>
          <textarea readOnly value={csv} style={{width:"100%",height:300,background:C.inp,color:C.text,border:`1px solid ${C.border}`,borderRadius:8,padding:10,fontSize:10,fontFamily:"monospace",resize:"none",boxSizing:"border-box"}}/>
        </div>
        <div style={{padding:"10px 14px",borderTop:`1px solid ${C.border}`,display:"flex",gap:8}}>
          <button onClick={copy} style={{...btn("p",0),flex:1}}>{copied?"✅ Copied!":"📋 Copy to clipboard"}</button>
          <button onClick={onClose} style={{...btn("s",0),flex:1}}>Close</button>
        </div>
      </div>
    </div>
  );
}

// ─── USER DETAIL ─────────────────────────────────────────────────────────────
function buildUserCSV(user) {
  const tips = user.tips || {};
  const rows = [];
  rows.push(["FootieFriend – Tips for: " + user.name]);
  rows.push([]);
  rows.push(["── MATCH PREDICTIONS (1/X/2) ──"]);
  rows.push(["Date","Group","Home","Away","Tip"]);
  SCHEDULE.forEach(day => day.matches.forEach(m => rows.push([day.date, m.g, m.home, m.away, tips.matches?.[m.id]||"-"])));
  rows.push([]);
  rows.push(["── GROUP RANKINGS ──"]);
  rows.push(["Group","1st","2nd","3rd","4th"]);
  Object.keys(GROUPS).forEach(g=>{const r=tips.groupRankings?.[g]||[];rows.push([`Group ${g}`,r[0]||"-",r[1]||"-",r[2]||"-",r[3]||"-"]);});
  rows.push([]);
  rows.push(["── BEST THIRD-PLACE PICKS ──"]);
  (tips.thirdPlace||[]).forEach(t=>rows.push([t]));
  rows.push([]);
  rows.push(["── KNOCKOUT BRACKET ──"]);
  ["R32","R16","QF","SF","Final"].forEach(rd=>{rows.push([rd,...(tips.knockout?.[rd]||[])]);});
  rows.push(["Winner", tips.winner||"-"]);
  rows.push([]);
  rows.push(["── SPECIALS ──"]);
  rows.push(["Top Scorer", tips.topScorer||"-"]);
  rows.push(["MVP", tips.mvp||"-"]);
  rows.push(["Dass-Loppa", tips.dass||"-"]);
  return rows.map(r=>r.map(c=>{const s=String(c??"");return s.includes(",")||s.includes('"')?`"${s.replace(/"/g,'""')}"`  :s;}).join(",")).join("\n");
}

function exportUserToExcel(user, onShow) {
  onShow(buildUserCSV(user), `tips_${user.name}.csv`);
}

function UserDetail({user, onBack, onExport}) {
  const tips = user.tips || {};
  const Section = ({title,children}) => (
    <div style={{...card,marginBottom:8}}>
      <div style={{fontWeight:800,fontSize:12,color:C.accent,marginBottom:8,letterSpacing:1}}>{title}</div>
      {children}
    </div>
  );
  const Row = ({label,value}) => (
    <div style={{display:"flex",justifyContent:"space-between",padding:"4px 0",borderBottom:`1px solid ${C.border}`,fontSize:12}}>
      <span style={{color:C.muted}}>{label}</span>
      <span style={{fontWeight:600,textAlign:"right",maxWidth:"60%"}}>{value||<span style={{color:C.border}}>–</span>}</span>
    </div>
  );

  return(
    <div>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:14}}>
        <div>
          <button onClick={onBack} style={{...btn("s",0),width:"auto",padding:"5px 10px",fontSize:11}}>← Back</button>
        </div>
        <div style={{fontWeight:900,fontSize:16}}>{user.name}</div>
        <button onClick={onExport} style={{...btn("g",0),width:"auto",padding:"5px 10px",fontSize:11}}>📊 Export</button>
      </div>

      <Section title="⚽ MATCH PREDICTIONS">
        {SCHEDULE.map(day=>(
          <div key={day.date} style={{marginBottom:8}}>
            <div style={{fontSize:10,color:C.gold,fontWeight:700,marginBottom:4}}>📅 {day.date}</div>
            {day.matches.map(m=>{
              const tip=tips.matches?.[m.id];
              return(
                <div key={m.id} style={{display:"flex",alignItems:"center",justifyContent:"space-between",padding:"3px 0",borderBottom:`1px solid ${C.border}`}}>
                  <span style={{fontSize:11,flex:1}}>{fl(m.home)} vs {fl(m.away)}</span>
                  <span style={{fontWeight:700,fontSize:12,color:tip==="X"?C.gold:tip?C.accent:C.muted,marginLeft:8}}>
                    {tip||"–"}
                  </span>
                </div>
              );
            })}
          </div>
        ))}
      </Section>

      <Section title="📊 GROUP RANKINGS">
        {Object.entries(GROUPS).map(([g])=>{
          const r=tips.groupRankings?.[g]||[];
          return(
            <div key={g} style={{display:"flex",gap:6,alignItems:"center",padding:"4px 0",borderBottom:`1px solid ${C.border}`}}>
              <span style={{fontSize:11,color:C.muted,width:60,fontWeight:700}}>Group {g}</span>
              {[0,1,2,3].map(i=>(
                <span key={i} style={{flex:1,fontSize:10,textAlign:"center",padding:"2px 4px",borderRadius:5,background:r[i]?i===0?"#14532d":i===1?"#1e3a5f":i===2?"#431407":"#1a1a2e":C.inp,color:r[i]?C.text:C.border}}>
                  {r[i]?`${i+1}. ${fl(r[i])} ${short(r[i])}`:`${i+1}.`}
                </span>
              ))}
            </div>
          );
        })}
      </Section>

      <Section title="3️⃣ THIRD PLACE PICKS">
        <div style={{display:"flex",flexWrap:"wrap",gap:4}}>
          {(tips.thirdPlace||[]).length===0
            ? <span style={{color:C.muted,fontSize:12}}>None selected</span>
            : (tips.thirdPlace||[]).map(t=><span key={t} style={{padding:"3px 8px",borderRadius:6,background:C.aD,fontSize:11,fontWeight:600}}>{fl(t)} {t}</span>)}
        </div>
      </Section>

      <Section title="🥊 KNOCKOUT BRACKET">
        {["R32","R16","QF","SF","Final"].map(rd=>{
          const picks=tips.knockout?.[rd]||[];
          return(
            <div key={rd} style={{marginBottom:6}}>
              <div style={{fontSize:10,color:C.muted,fontWeight:700,marginBottom:3}}>{rd}</div>
              <div style={{display:"flex",flexWrap:"wrap",gap:3}}>
                {picks.length===0
                  ? <span style={{color:C.border,fontSize:11}}>–</span>
                  : picks.map(t=><span key={t} style={{padding:"2px 7px",borderRadius:5,background:C.inp,fontSize:11}}>{fl(t)} {short(t)}</span>)}
              </div>
            </div>
          );
        })}
        <Row label="🏆 Winner" value={tips.winner?tf(tips.winner):null}/>
      </Section>

      <Section title="⭐ SPECIALS & 💩 DASS">
        <Row label="Top Scorer" value={tips.topScorer}/>
        <Row label="MVP" value={tips.mvp}/>
        <Row label="Dass-Loppa" value={tips.dass?tf(tips.dass):null}/>
      </Section>
    </div>
  );
}

// ─── ADMIN ────────────────────────────────────────────────────────────────────
function Admin({results,users:appUsers,lobbies:appLobbies,onSave,onExit,onExport,onRemoveFromGroup,onDeleteUser}){
  const [confirmRemove,setConfirmRemove]=useState(null);
  const [selectedUser,setSelectedUser]=useState(null);
  const [csvModal,setCsvModal]=useState(null);
  const showCSV=(csv,filename)=>setCsvModal({csv,filename});
  const onGetLobbies=()=>appLobbies||[];
  const base={matches:{},groupRankings:{},advancingThirds:[],knockout:{R32:[],R16:[],QF:[],SF:[],Final:[],Winner:null},goals:{},knockoutRounds:{},topScorer:"",mvp:""};
  const [tab,setTab]=useState("matches");
  const [r,setR]=useState({...base,...JSON.parse(JSON.stringify(results))});
  const [saved,setSaved]=useState(false);
  const sMR=(id,side,val)=>setR(p=>({...p,matches:{...p.matches,[id]:{...(p.matches[id]||{home:"",away:""}),[side]:val===""?"":parseInt(val)||0}}}));
  const tKO=(rd,t,max)=>setR(p=>{const c=p.knockout[rd]||[];const sel=c.includes(t);return{...p,knockout:{...p.knockout,[rd]:sel?c.filter(x=>x!==t):c.length<max?[...c,t]:c}};});
  const tGR=(g,t)=>setR(p=>{const c=[...(p.groupRankings?.[g]||[])];const i=c.indexOf(t);if(i>=0)c.splice(i,1);else if(c.length<4)c.push(t);return{...p,groupRankings:{...p.groupRankings,[g]:c}};});
  const tT3=t=>setR(p=>{const c=p.advancingThirds||[];const s=c.includes(t);return{...p,advancingThirds:s?c.filter(x=>x!==t):c.length<8?[...c,t]:c};});
  const tabs=[{id:"matches",l:"Matches"},{id:"groups",l:"Rankings"},{id:"thirds",l:"3rd Adv."},{id:"knockout",l:"Knockout"},{id:"dass",l:"Dass"},{id:"special",l:"Specials"},{id:"users",l:"👥 Users"}];
  return(
    <div style={{padding:12,maxWidth:500,margin:"0 auto"}}>
      <div style={{display:"flex",justifyContent:"space-between",alignItems:"center",marginBottom:12}}>
        <div style={{fontWeight:900,fontSize:16,color:C.accent}}>🔧 Admin Panel</div>
        <button onClick={onExit} style={{...btn("s",0),width:"auto",padding:"6px 10px",fontSize:11}}>← Exit</button>
      </div>
      <div style={{display:"flex",gap:3,marginBottom:12,overflowX:"auto"}}>
        {tabs.map(t=><button key={t.id} onClick={()=>setTab(t.id)} style={{...btn(tab===t.id?"p":"s",0),flex:"0 0 auto",width:"auto",padding:"6px 10px",fontSize:11}}>{t.l}</button>)}
      </div>
      {tab==="matches"&&SCHEDULE.map(day=>(
        <div key={day.date}>
          <div style={{fontSize:10,color:C.gold,fontWeight:800,letterSpacing:1,margin:"10px 0 4px"}}>📅 {day.date}</div>
          {day.matches.map(m=>(
            <div key={m.id} style={{...card,padding:8,marginBottom:4}}>
              <div style={{display:"flex",alignItems:"center",gap:4,fontSize:11}}>
                <span style={{flex:1,textAlign:"right"}}>{fl(m.home)} {short(m.home)}</span>
                <input type="number" min={0} style={{...inp,width:34,textAlign:"center",padding:"4px",marginTop:0,fontSize:14}} value={r.matches[m.id]?.home??""} onChange={e=>sMR(m.id,"home",e.target.value)}/>
                <span style={{color:C.muted}}>–</span>
                <input type="number" min={0} style={{...inp,width:34,textAlign:"center",padding:"4px",marginTop:0,fontSize:14}} value={r.matches[m.id]?.away??""} onChange={e=>sMR(m.id,"away",e.target.value)}/>
                <span style={{flex:1}}>{fl(m.away)} {short(m.away)}</span>
              </div>
            </div>
          ))}
        </div>
      ))}
      {tab==="groups"&&Object.entries(GROUPS).map(([g,teams])=>{
        const ranked=r.groupRankings?.[g]||[];
        return(<div key={g} style={card}><div style={{fontWeight:800,fontSize:12,color:C.accent,marginBottom:6}}>GROUP {g}</div><div style={{display:"flex",flexWrap:"wrap",gap:3}}>{teams.map(t=>{const pos=ranked.indexOf(t);const sel=pos>=0;return(<button key={t} onClick={()=>tGR(g,t)} style={{padding:"4px 8px",borderRadius:6,border:`1px solid ${sel?C.accent:C.border}`,background:sel?C.aD:C.inp,color:C.text,cursor:"pointer",fontSize:11,fontWeight:sel?700:400}}>{fl(t)} {short(t)} {sel&&`(${pos+1})`}</button>);})}</div></div>);
      })}
      {tab==="thirds"&&(
        <div>
          <div style={{fontSize:14,fontWeight:800,color:C.accent,marginBottom:8}}>Mark 8 Advancing Thirds ({(r.advancingThirds||[]).length}/8)</div>
          {Object.keys(GROUPS).map(g=>{const team=(r.groupRankings?.[g]||[])[2];if(!team)return <div key={g} style={{...card,color:C.muted,fontSize:11,padding:8}}>Group {g} – rank first</div>;const sel=(r.advancingThirds||[]).includes(team);return(<button key={g} onClick={()=>tT3(team)} style={{display:"flex",alignItems:"center",gap:8,width:"100%",padding:"8px 10px",marginBottom:4,borderRadius:8,cursor:"pointer",background:sel?C.aD:C.inp,border:`1px solid ${sel?C.accent:C.border}`,color:C.text,fontWeight:sel?700:400}}><span style={{fontSize:10,color:C.muted,width:20}}>G{g}</span><span style={{fontSize:15}}>{fl(team)}</span><span style={{flex:1,fontSize:12}}>{team}</span>{sel&&<span style={{color:C.accent}}>✓ Advanced</span>}</button>);})}
        </div>
      )}
      {tab==="knockout"&&(
        <div>
          <div style={{fontSize:14,fontWeight:800,color:C.accent,marginBottom:8}}>Official Knockout Results</div>
          {[{rd:"R32",max:16},{rd:"R16",max:8},{rd:"QF",max:4},{rd:"SF",max:2},{rd:"Final",max:2}].map(({rd,max})=>(
            <div key={rd} style={card}><div style={{fontWeight:700,marginBottom:6}}>{rd} ({(r.knockout[rd]||[]).length}/{max})</div><div style={{display:"flex",flexWrap:"wrap",gap:3}}>{ALL_TEAMS.map(t=>{const sel=(r.knockout[rd]||[]).includes(t);return(<button key={t} onClick={()=>tKO(rd,t,max)} style={{padding:"3px 6px",borderRadius:5,border:`1px solid ${sel?C.accent:C.border}`,background:sel?C.aD:C.inp,color:C.text,cursor:"pointer",fontSize:10,fontWeight:sel?700:400}}>{fl(t)} {short(t)}</button>);})}</div></div>
          ))}
          <div style={card}><div style={{fontWeight:700,marginBottom:6}}>🏆 Winner</div><div style={{display:"flex",flexWrap:"wrap",gap:3}}>{ALL_TEAMS.map(t=>{const sel=r.knockout.Winner===t;return(<button key={t} onClick={()=>setR(p=>({...p,knockout:{...p.knockout,Winner:sel?null:t}}))} style={{padding:"4px 8px",borderRadius:6,border:`2px solid ${sel?C.gold:C.border}`,background:sel?C.gD:C.inp,color:sel?C.gold:C.text,cursor:"pointer",fontSize:11,fontWeight:sel?800:400}}>{fl(t)} {short(t)} {sel&&"🏆"}</button>);})}</div></div>
        </div>
      )}
      {tab==="dass"&&(
        <div>
          <div style={card}><div style={{fontWeight:700,color:C.red,marginBottom:8}}>Goals per team</div>{ALL_TEAMS.map(t=>(<div key={t} style={{display:"flex",alignItems:"center",gap:8,marginBottom:4}}><span style={{flex:1,fontSize:11}}>{fl(t)} {t}</span><input type="number" min={0} style={{...inp,width:48,textAlign:"center",padding:"4px",marginTop:0}} value={r.goals?.[t]??0} onChange={e=>setR(p=>({...p,goals:{...p.goals,[t]:parseInt(e.target.value)||0}}))}/></div>))}</div>
          <div style={card}><div style={{fontWeight:700,color:C.red,marginBottom:8}}>Knockout rounds advanced</div>{ALL_TEAMS.map(t=>(<div key={t} style={{display:"flex",alignItems:"center",gap:8,marginBottom:4}}><span style={{flex:1,fontSize:11}}>{fl(t)} {t}</span><input type="number" min={0} style={{...inp,width:48,textAlign:"center",padding:"4px",marginTop:0}} value={r.knockoutRounds?.[t]??0} onChange={e=>setR(p=>({...p,knockoutRounds:{...p.knockoutRounds,[t]:parseInt(e.target.value)||0}}))}/></div>))}</div>
        </div>
      )}
      {tab==="special"&&(
        <div>
          {["topScorer","mvp"].map(field=>{
            const label=field==="topScorer"?"⚽ Top Scorer (Golden Boot)":"🌟 Best Player (Golden Ball)";
            const norm=s=>s.trim().toLowerCase().normalize("NFD").replace(/[\u0300-\u036f]/g,"").replace(/[^a-z0-9]/g,"");
            const allTips=[...new Set((appUsers||[]).map(u=>u.tips?.[field]).filter(Boolean).map(s=>s.trim()))].sort();
            // Store as array of accepted norms
            const accepted=r[field+"Accepted"]||[];
            const groups={};
            allTips.forEach(tip=>{const n=norm(tip);if(!groups[n])groups[n]=[];groups[n].push(tip);});
            const toggle=(n)=>setR(p=>({...p,[field+"Accepted"]:accepted.includes(n)?accepted.filter(x=>x!==n):[...accepted,n]}));
            return(
              <div key={field} style={card}>
                <div style={{fontWeight:700,marginBottom:4}}>{label}</div>
                <div style={{fontSize:11,color:C.muted,marginBottom:10}}>Tap to mark correct answers. You can select multiple – all matching spellings get points. <b style={{color:C.accent}}>{accepted.length} selected.</b></div>
                {allTips.length===0&&<div style={{fontSize:11,color:C.muted}}>No tips submitted yet.</div>}
                {Object.entries(groups).map(([n,tips])=>{
                  const sel=accepted.includes(n);
                  return(
                    <button key={n} onClick={()=>toggle(n)} style={{display:"flex",alignItems:"center",gap:8,width:"100%",textAlign:"left",padding:"8px 10px",borderRadius:8,cursor:"pointer",border:`1px solid ${sel?C.accent:C.border}`,background:sel?C.aD:C.inp,color:C.text,fontWeight:sel?700:400,marginBottom:4}}>
                      <span style={{fontSize:16,color:sel?C.accent:C.muted}}>{sel?"✓":"○"}</span>
                      <span style={{flex:1}}>
                        <span style={{fontSize:13}}>{tips[0]}</span>
                        {tips.length>1&&<span style={{fontSize:10,color:C.muted,marginLeft:6}}>also: {tips.slice(1).join(", ")}</span>}
                      </span>
                    </button>
                  );
                })}
              </div>
            );
          })}
        </div>
      )}
      {tab==="users"&&(
        <div>
          <div style={{fontSize:14,fontWeight:800,color:C.accent,marginBottom:8}}>👥 Manage Users</div>
          {selectedUser
            ? <UserDetail user={selectedUser} onBack={()=>setSelectedUser(null)} onExport={()=>exportUserToExcel(selectedUser,showCSV)}/>
            : <div>
                <div style={{fontSize:12,color:C.muted,marginBottom:12}}>Tap a player to see their tips. Remove from group or delete entirely.</div>
                {(appUsers||[]).length===0&&<div style={{...card,textAlign:"center",color:C.muted}}>No users yet.</div>}
                {(appUsers||[]).map(u=>{
                  const userGroups=(u.groups||[]).map(code=>{
                    const lobby=(appLobbies||[]).find(l=>l.code===code);
                    return{code,name:lobby?.name||code};
                  });
                  return(
                    <div key={u.id} style={{...card,cursor:"pointer"}} onClick={e=>{if(e.target.tagName!=="BUTTON")setSelectedUser(u);}}>
                      <div style={{fontWeight:700,fontSize:13,marginBottom:6}}>{u.name}</div>
                      {userGroups.length===0&&<div style={{fontSize:11,color:C.muted}}>Not in any groups</div>}
                      {userGroups.map(g=>(
                        <div key={g.code} style={{display:"flex",alignItems:"center",justifyContent:"space-between",padding:"6px 8px",background:C.inp,borderRadius:7,marginBottom:4}}>
                          <div>
                            <span style={{fontSize:12,fontWeight:600}}>{g.name}</span>
                            <span style={{fontSize:10,color:C.muted,marginLeft:6}}>{g.code}</span>
                          </div>
                          <button onClick={()=>{const key=`${u.id}-${g.code}`;if(confirmRemove===key){onRemoveFromGroup(u.id,g.code);setConfirmRemove(null);}else{setConfirmRemove(key);setTimeout(()=>setConfirmRemove(null),4000);}}} style={{padding:"4px 10px",borderRadius:6,border:"none",cursor:"pointer",fontSize:11,fontWeight:700,background:confirmRemove===`${u.id}-${g.code}`?C.red:C.rD,color:confirmRemove===`${u.id}-${g.code}`?"#fff":C.red}}>
                            {confirmRemove===`${u.id}-${g.code}`?"⚠️ Confirm":"Remove from group"}
                          </button>
                        </div>
                      ))}
                      <div style={{marginTop:6,textAlign:"right"}}>
                        <button onClick={()=>{const key=`delete-${u.id}`;if(confirmRemove===key){onDeleteUser(u.id);setConfirmRemove(null);}else{setConfirmRemove(key);setTimeout(()=>setConfirmRemove(null),4000);}}} style={{padding:"4px 12px",borderRadius:6,border:`1px solid ${C.red}`,cursor:"pointer",fontSize:11,fontWeight:700,background:confirmRemove===`delete-${u.id}`?C.red:"transparent",color:confirmRemove===`delete-${u.id}`?"#fff":C.red}}>
                          {confirmRemove===`delete-${u.id}`?"⚠️ Confirm DELETE user":"🗑️ Delete user entirely"}
                        </button>
                      </div>
                    </div>
                  );
                })}
              </div>
          }
        </div>
      )}
      <button style={{...btn("g"),marginTop:14,fontSize:14,padding:"12px 0"}} onClick={()=>{onSave(r);setSaved(true);setTimeout(()=>setSaved(false),2000);}}>{saved?"✅ Saved!":"💾 Save All Results"}</button>
      <button style={{...btn("s"),marginTop:8,fontSize:14,padding:"12px 0",border:`1px solid ${C.accent}`,color:C.accent}} onClick={()=>onExport(r,showCSV)}>📊 Export to Excel</button>
      {csvModal&&<CSVModal csv={csvModal.csv} filename={csvModal.filename} onClose={()=>setCsvModal(null)}/>}
    </div>
  );
}

// ─── MAIN ─────────────────────────────────────────────────────────────────────
export default function FootieFriend(){
  const [users,setUsers]=useState([]);
  const [lobbies,setLobbies]=useState([]);
  const [results,setResults]=useState({});
  const [user,setUser]=useState(null);
  const [view,setView]=useState("auth");
  const [lobby,setLobby]=useState(null);
  const [notif,setNotif]=useState("");
  const [loading,setLoading]=useState(true);

  const notify=msg=>{setNotif(msg);setTimeout(()=>setNotif(""),2500);};
  const locked=new Date()>=LOCK_TIME;

  // Load all data from Supabase on mount
  useEffect(()=>{
    Promise.all([db.getUsers(),db.getLobbies(),db.getResults()])
      .then(([u,l,r])=>{setUsers(u);setLobbies(l);setResults(r);})
      .catch(e=>notify("Connection error: "+e.message))
      .finally(()=>setLoading(false));
  },[]);

  // Refresh data periodically (every 30s) so leaderboard stays live
  useEffect(()=>{
    const t=setInterval(()=>{
      db.getUsers().then(setUsers).catch(()=>{});
      db.getResults().then(setResults).catch(()=>{});
    },30000);
    return()=>clearInterval(t);
  },[]);

  const handleLogin=async(name,pin,isReg)=>{
    if(isReg){
      if(users.find(u=>u.name.toLowerCase()===name.toLowerCase())){notify("Name taken – try logging in.");return;}
      const u={id:Date.now().toString(),name,pin,tips:{},groups:[]};
      try{
        await db.upsertUser(u);
        setUsers(prev=>[...prev,u]);
        setUser(u);setView("lobby");
      }catch(e){notify("Error creating account: "+e.message);}
    } else {
      // Also refresh users from DB to get latest
      let allUsers=users;
      try{allUsers=await db.getUsers();setUsers(allUsers);}catch(_){}
      const u=allUsers.find(u=>u.name.toLowerCase()===name.toLowerCase()&&u.pin===pin);
      if(!u){notify("Wrong name or PIN.");return;}
      setUser(u);setView("lobby");
    }
  };

  const handleJoin=async code=>{
    const updated={...user,groups:[...(user.groups||[]),code]};
    await db.upsertUser(updated);
    setUsers(prev=>prev.map(u=>u.id===updated.id?updated:u));
    setUser(updated);
    notify("Joined! ✅");
  };

  const handleCreate=async name=>{
    const code=gc();
    const newLobby={code,name,created_by:user.id};
    const updated={...user,groups:[...(user.groups||[]),code]};
    await db.upsertLobby(newLobby);
    await db.upsertUser(updated);
    setLobbies(prev=>[...prev,newLobby]);
    setUsers(prev=>prev.map(u=>u.id===updated.id?updated:u));
    setUser(updated);
    notify(`Created! Code: ${code} 🎉`);
  };

  const handleSaveTips=async tips=>{
    const updated={...user,tips};
    await db.upsertUser(updated);
    setUsers(prev=>prev.map(u=>u.id===updated.id?updated:u));
    setUser(updated);
    notify("Tips saved! ✅");
  };

  const handleSaveResults=async r=>{
    await db.saveResults(r);
    setResults(r);
    notify("Results saved! ✅");
  };

  const handleRemoveFromGroup=async(uid,code)=>{
    const target=users.find(u=>u.id===uid);
    if(!target)return;
    const updated={...target,groups:(target.groups||[]).filter(g=>g!==code)};
    await db.upsertUser(updated);
    setUsers(prev=>prev.map(u=>u.id===uid?updated:u));
    if(user.id===uid)setUser(updated);
    notify("Removed from group ✅");
  };

  const handleDeleteUser=async uid=>{
    await db.deleteUser(uid);
    setUsers(prev=>prev.filter(u=>u.id!==uid));
    notify("User deleted ✅");
  };

  const activeLobby=lobby?lobbies.find(l=>l.code===lobby):null;
  const navItems=user?[{id:"lobby",icon:"🏠",label:"Groups"},{id:"tips",icon:"✏️",label:"My Tips"},...(lobby?[{id:"leaderboard",icon:"🏆",label:"Table"}]:[])]:[];

  if(loading) return(
    <div style={{minHeight:"100vh",background:C.bg,display:"flex",flexDirection:"column",alignItems:"center",justifyContent:"center",gap:16}}>
      <div style={{fontSize:48}}>⚽</div>
      <div style={{fontSize:18,fontWeight:800,color:C.accent}}>FootieFriend</div>
      <div style={{fontSize:13,color:C.muted}}>Loading...</div>
    </div>
  );

  return(
    <div style={{minHeight:"100vh",background:C.bg,color:C.text,fontFamily:"'Segoe UI',system-ui,sans-serif",paddingBottom:70}}>
      <div style={{background:"linear-gradient(135deg,#064e3b 0%,#0a0e1a 70%)",borderBottom:`1px solid ${C.border}`,padding:"16px 16px 12px",textAlign:"center"}}>
        <div style={{fontSize:24,fontWeight:900,letterSpacing:"-1px",color:C.accent}}>FootieFriend ⚽</div>
        <div style={{fontSize:10,color:C.muted,letterSpacing:3,textTransform:"uppercase"}}>World Cup 2026 Predictor</div>
        {locked&&<div style={{fontSize:10,color:C.red,marginTop:3,fontWeight:700}}>🔒 Tips Locked</div>}
      </div>
      {notif&&<div style={{background:C.accent,color:"#000",textAlign:"center",padding:"8px",fontSize:12,fontWeight:700,position:"sticky",top:0,zIndex:100}}>{notif}</div>}
      {user&&<div style={{display:"flex",background:C.card,borderBottom:`1px solid ${C.border}`,position:"sticky",top:0,zIndex:50}}>
        {navItems.map(n=><button key={n.id} onClick={()=>setView(n.id)} style={{flex:1,padding:"10px 4px 8px",background:"transparent",border:"none",borderBottom:`2px solid ${view===n.id?C.accent:"transparent"}`,color:view===n.id?C.accent:C.muted,cursor:"pointer"}}><div style={{fontSize:18}}>{n.icon}</div><div style={{fontSize:9,fontWeight:600,marginTop:1}}>{n.label}</div></button>)}
      </div>}
      {view==="auth"&&<Auth onLogin={handleLogin} onAdmin={()=>setView("admin")}/>}
      {view==="admin"&&<Admin results={results} users={users} lobbies={lobbies} onSave={handleSaveResults} onExit={()=>setView("auth")} onExport={(r,show)=>exportToExcel({users,lobbies},r,show)} onRemoveFromGroup={handleRemoveFromGroup} onDeleteUser={handleDeleteUser}/>}
      {view==="lobby"&&user&&<Lobbies user={user} lobbies={lobbies} onJoin={handleJoin} onCreate={handleCreate} onEnter={code=>{setLobby(code);setView("leaderboard");}} onLogout={()=>{setUser(null);setView("auth");}}/>}
      {view==="tips"&&user&&<TipsForm user={user} locked={locked} onSave={handleSaveTips}/>}
      {view==="leaderboard"&&activeLobby&&<Leaderboard lobby={activeLobby} users={users} results={results}/>}
    </div>
  );
}
