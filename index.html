import React, { useEffect, useMemo, useRef, useState } from "react";
import { motion, AnimatePresence } from "framer-motion";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Tabs, TabsContent, TabsList, TabsTrigger } from "@/components/ui/tabs";
import { Button } from "@/components/ui/button";
import { Badge } from "@/components/ui/badge";
import { Progress } from "@/components/ui/progress";
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select";
import { Input } from "@/components/ui/input";
import { Trophy, Brain, Gamepad2, CheckCircle2, XCircle, BookText, Sparkles, Coins, Timer, Star, Swords, Keyboard } from "lucide-react";

// =============================
// Helpers & Store
// =============================
const rand = (min:number, max:number) => Math.floor(Math.random() * (max - min + 1)) + min;
const pick = <T,>(arr:T[]) => arr[rand(0, arr.length-1)];
const shuffle = <T,>(arr:T[]) => [...arr].sort(() => Math.random() - 0.5);

function useStore(){
  const [xp, setXp] = useState(0);
  const [coins, setCoins] = useState(0);
  const [streak, setStreak] = useState(0);
  const [history, setHistory] = useState<{day:string, xp:number}[]>([]);
  useEffect(()=>{
    const today = new Date().toLocaleDateString();
    setHistory(h => h.find(r=>r.day===today) ? h : [...h, {day:today, xp:0}].slice(-14));
  },[]);
  const award = (x:number,c=0)=>{
    setXp(v=>v+x); setCoins(v=>v+c); setStreak(s=>s+1);
    const today = new Date().toLocaleDateString();
    setHistory(h=>h.map(r=>r.day===today?{...r, xp:r.xp + x}:r));
  };
  const miss = ()=> setStreak(0);
  const level = Math.floor(xp/250)+1;
  return { xp, coins, streak, history, level, award, miss };
}

// =============================
// Content – VWO 2 Nederlands
// =============================
// Werkwoordspelling – tegenwoordige tijd (ik/hij/zij) & voltooid deelwoord
const VERB_FORMS = [
  { inf:"worden", subject:"hij", correct:"wordt", distractors:["word","wordt"], rule:"tt: stam + t bij hij/zij/het" },
  { inf:"lopen", subject:"ik", correct:"loop", distractors:["loopt","lope"], rule:"tt: ik-vorm = stam" },
  { inf:"maken", subject:"hij", correct:"maakt", distractors:["maak","maakt"], rule:"tt: stam + t" },
  { inf:"praten", subject:"hij", correct:"praat", distractors:["praat","praatt"], rule:"tt: stam + t (let op dubbel a)" },
  { inf:"fietsen", subject:"zij", correct:"fietst", distractors:["fiets","fietst"], rule:"tt: stam + t" },
  { inf:"reizen", subject:"ik", correct:"reis", distractors:["reist","reiss"], rule:"tt: ik-vorm = stam" },
  { inf:"antwoorden", subject:"hij", correct:"antwoordt", distractors:["antwoord","antwoort"], rule:"tt: stam + t, geen extra d" },
];

const PAST_PARTICIPLE = [
  // 't kofschip/x regel: eindigt stam op f, s, ch, p, t, k, x → ge- + stam + t
  { inf:"fietsen", correct:"gefietst", wrong:["gefietsD","gefietsT"], hint:"'t kofschip: stam eindigt op s → -t" },
  { inf:"werken", correct:"gewerkt", wrong:["gewerkD","gewerkT"], hint:"stam eindigt op k → -t" },
  { inf:"leven", correct:"geleefd", wrong:["geleeft","geleevd"], hint:"stam eindigt op v → -d (v→f in uitspraak)" },
  { inf:"reizen", correct:"gereisd", wrong:["gereist","gereizd"], hint:"stam eindigt op z → -d (z→s in uitspraak)" },
  { inf:"pakken", correct:"gepakt", wrong:["gepakd","gepakt"], hint:"stam eindigt op k → -t" },
];

const COMPOUNDS = [
  { base:"aardappel + puree", correct:"aardappelpuree", wrong:["aardappel puree","aardappel-puree"], hint:"samenstelling = aan elkaar" },
  { base:"bioscoop + kaartje", correct:"bioscoopkaartje", wrong:["bioscoop kaartje","bioscoop-kaartje"], hint:"samenstelling = aan elkaar" },
  { base:"lange-afstand + loper", correct:"langeafstandsloper", wrong:["lange afstandsloper","lange-afstandsloper"], hint:"koppeltekens alleen bij duidelijkheid" },
];

const GRAMMAR_GOOD_BAD = [
  { good:"Hij heeft meer tijd dan ik.", bad:"Hij heeft meer tijd als ik.", hint:"Vergelijking → dan, geen als" },
  { good:"Dat is het boek dat ik zocht.", bad:"Dat is het boek wat ik zocht.", hint:"Betrekkelijk voornaamwoord bij 'het boek' → dat" },
  { good:"Er liggen minder boeken op tafel.", bad:"Er liggen mindere boeken op tafel.", hint:"Minder bij hoeveelheden" },
  { good:"Ik ben groter dan hij.", bad:"Ik ben groter als hem.", hint:"Vergelijking → dan; naamvallen: dan hij" },
];

// =============================
// Root App
// =============================
export default function NederNinja(){
  const store = useStore();
  const [tab, setTab] = useState("oefenen");
  const [theme, setTheme] = useState("from-indigo-600 to-cyan-600");
  return (
    <div className="min-h-screen text-white relative">
      <div className={`fixed inset-0 -z-10 bg-gradient-to-br ${theme}`} />
      <header className="max-w-6xl mx-auto p-6 flex items-center justify-between">
        <div className="flex items-center gap-3">
          <Gamepad2 className="w-7 h-7"/>
          <h1 className="text-2xl md:text-3xl font-bold tracking-tight">NederNinja — VWO 2</h1>
          <Badge className="bg-white/20 ml-2">prototype</Badge>
        </div>
        <div className="flex items-center gap-3">
          <Badge className="bg-black/30"><Star className="w-4 h-4 mr-1"/>Lv {Math.floor(store.xp/250)+1}</Badge>
          <Badge className="bg-black/30"><Coins className="w-4 h-4 mr-1"/>{store.coins}</Badge>
          <Badge className="bg-black/30"><Trophy className="w-4 h-4 mr-1"/>XP {store.xp}</Badge>
          <Badge className="bg-black/30"><Timer className="w-4 h-4 mr-1"/>Streak {store.streak}</Badge>
        </div>
      </header>

      <main className="max-w-6xl mx-auto p-6">
        <Tabs value={tab} onValueChange={setTab}>
          <TabsList className="bg-black/20 grid grid-cols-3">
            <TabsTrigger value="oefenen">Oefenen</TabsTrigger>
            <TabsTrigger value="minigames">Minigames</TabsTrigger>
            <TabsTrigger value="voortgang">Voortgang</TabsTrigger>
          </TabsList>

          <TabsContent value="oefenen" className="mt-6">
            <ExerciseHub store={store} />
          </TabsContent>

          <TabsContent value="minigames" className="mt-6">
            <MiniGames store={store} />
          </TabsContent>

          <TabsContent value="voortgang" className="mt-6">
            <ProgressView store={store} />
          </TabsContent>
        </Tabs>
      </main>

      <footer className="max-w-6xl mx-auto p-6 pt-0 text-sm text-white/80">
        Gebouwd voor leren met fun. Data is tijdelijk en wordt lokaal bijgehouden.
      </footer>
    </div>
  );
}

// =============================
// Exercises
// =============================
function ExerciseHub({store}:{store:ReturnType<typeof useStore>}){
  const [mode, setMode] = useState("werkwoordspelling");
  return (
    <div className="grid lg:grid-cols-3 gap-6">
      <Card className="bg-white/10 border-white/20 lg:col-span-2">
        <CardHeader>
          <CardTitle className="flex items-center gap-2"><BookText className="w-5 h-5"/> Oefenen — {label(mode)}</CardTitle>
        </CardHeader>
        <CardContent>
          {mode==="werkwoordspelling" && <VerbExercise store={store}/>} 
          {mode==="voltooid" && <ParticipleExercise store={store}/>} 
          {mode==="samenstellingen" && <CompoundExercise store={store}/>} 
          {mode==="grammatica" && <GrammarExercise store={store}/>} 
        </CardContent>
      </Card>

      <Card className="bg-white/10 border-white/20">
        <CardHeader>
          <CardTitle className="flex items-center gap-2"><Brain className="w-5 h-5"/> Kies onderdeel</CardTitle>
        </CardHeader>
        <CardContent className="space-y-3">
          <Select value={mode} onValueChange={setMode}>
            <SelectTrigger className="bg-black/30 border-white/20">
              <SelectValue />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value="werkwoordspelling">Werkwoordspelling (tt)</SelectItem>
              <SelectItem value="voltooid">Voltooid deelwoord</SelectItem>
              <SelectItem value="samenstellingen">Samenstellingen</SelectItem>
              <SelectItem value="grammatica">Grammatica: goed/fout</SelectItem>
            </SelectContent>
          </Select>
          <TipsBlock mode={mode} />
        </CardContent>
      </Card>
    </div>
  );
}

function label(m:string){
  switch(m){
    case "werkwoordspelling": return "Werkwoordspelling (tt)";
    case "voltooid": return "Voltooid deelwoord";
    case "samenstellingen": return "Samenstellingen";
    case "grammatica": return "Grammatica";
    default: return m;
  }
}

function TipsBlock({mode}:{mode:string}){
  const map:Record<string,string[]> = {
    werkwoordspelling:[
      "ik-vorm = stam (ik loop)",
      "hij/zij/het = stam + t (hij loopt)",
      "bij jij/je achter persoonsvorm komt soms geen -t: loop je?",
    ],
    voltooid:[
      "'t kofschip-x: f, s, ch, p, t, k, x → -t",
      "anders → -d (let op v→f, z→s in uitspraak)",
    ],
    samenstellingen:[
      "Samenstellingen schrijf je aan elkaar: bioscoopkaartje",
      "Gebruik een koppelteken alleen voor duidelijkheid of uitspraak",
    ],
    grammatica:[
      "Vergelijking: dan (niet als)",
      "Bij 'het-woorden' vaak 'dat' als betrekkelijk vnw",
    ],
  };
  return (
    <div className="text-sm text-white/90 space-y-2">
      <div className="font-semibold">Snelle tips</div>
      <ul className="list-disc pl-4 space-y-1">
        {map[mode].map((t,i)=>(<li key={i}>{t}</li>))}
      </ul>
    </div>
  );
}

function ChoiceRow({options,onPick}:{options:string[], onPick:(v:string)=>void}){
  return (
    <div className="grid md:grid-cols-2 gap-3">
      {options.map((o,i)=>
        <Button key={i} onClick={()=>onPick(o)} className="bg-black/40 border border-white/20 justify-start">
          {o}
        </Button>
      )}
    </div>
  );
}

function VerbExercise({store}:{store:ReturnType<typeof useStore>}){
  const [q, setQ] = useState(()=>pick(VERB_FORMS));
  const [feedback, setFeedback] = useState<string|null>(null);
  const options = useMemo(()=>shuffle([q.correct, ...shuffle(q.distractors).slice(0,2)]),[q]);
  const next=()=>{ setQ(pick(VERB_FORMS)); setFeedback(null); };
  const pickAns=(v:string)=>{
    if(v===q.correct){ setFeedback("goed"); store.award(12,1); }
    else { setFeedback("fout"); store.miss(); }
  };
  return (
    <div className="space-y-4">
      <div className="text-lg">Vul in (tt): <span className="font-semibold">{q.subject}</span> … <span className="italic">({q.inf})</span></div>
      <ChoiceRow options={options} onPick={pickAns} />
      <Feedback feedback={feedback} hint={q.rule} onNext={next} />
    </div>
  );
}

function ParticipleExercise({store}:{store:ReturnType<typeof useStore>}){
  const [q, setQ] = useState(()=>pick(PAST_PARTICIPLE));
  const [fb, setFb] = useState<string|null>(null);
  const options = useMemo(()=>shuffle([q.correct, ...q.wrong]),[q]);
  const next=()=>{ setQ(pick(PAST_PARTICIPLE)); setFb(null); };
  const pickAns=(v:string)=>{ if(v===q.correct){ setFb("goed"); store.award(12,1);} else { setFb("fout"); store.miss(); } };
  return (
    <div className="space-y-4">
      <div className="text-lg">Kies het juiste **voltooid deelwoord** voor <span className="italic">{q.inf}</span>.</div>
      <ChoiceRow options={options} onPick={pickAns} />
      <Feedback feedback={fb} hint={q.hint} onNext={next} />
    </div>
  );
}

function CompoundExercise({store}:{store:ReturnType<typeof useStore>}){
  const [q,setQ]=useState(()=>pick(COMPOUNDS));
  const [fb,setFb]=useState<string|null>(null);
  const options = useMemo(()=>shuffle([q.correct, ...q.wrong]),[q]);
  const next=()=>{ setQ(pick(COMPOUNDS)); setFb(null); };
  const pickAns=(v:string)=>{ if(v===q.correct){ setFb("goed"); store.award(10,1);} else { setFb("fout"); store.miss(); } };
  return (
    <div className="space-y-4">
      <div className="text-lg">Schrijf als samenstelling: <span className="italic">{q.base}</span></div>
      <ChoiceRow options={options} onPick={pickAns} />
      <Feedback feedback={fb} hint={q.hint} onNext={next} />
    </div>
  );
}

function GrammarExercise({store}:{store:ReturnType<typeof useStore>}){
  const [q, setQ] = useState(()=>pick(GRAMMAR_GOOD_BAD));
  const [fb, setFb] = useState<string|null>(null);
  const options = useMemo(()=>shuffle([q.good, q.bad]),[q]);
  const next=()=>{ setQ(pick(GRAMMAR_GOOD_BAD)); setFb(null); };
  const pickAns=(v:string)=>{ if(v===q.good){ setFb("goed"); store.award(12,1);} else { setFb("fout"); store.miss(); } };
  return (
    <div className="space-y-4">
      <div className="text-lg">Kies de **juiste** zin.</div>
      <ChoiceRow options={options} onPick={pickAns} />
      <Feedback feedback={fb} hint={q.hint} onNext={next} />
    </div>
  );
}

function Feedback({feedback, hint, onNext}:{feedback:string|null, hint?:string, onNext:()=>void}){
  return (
    <AnimatePresence>
      {feedback && (
        <motion.div initial={{opacity:0, y:8}} animate={{opacity:1, y:0}} exit={{opacity:0,y:-8}} className={`p-4 rounded-2xl border ${feedback==="goed"?"bg-emerald-500/20 border-emerald-400/40":"bg-rose-500/20 border-rose-400/40"}`}>
          <div className="flex items-center gap-2 font-semibold">
            {feedback==="goed"? <CheckCircle2 className="w-5 h-5"/> : <XCircle className="w-5 h-5"/>}
            {feedback==="goed"? "Goed gedaan!" : "Bijna!"}
          </div>
          {hint && <div className="text-sm mt-1">Tip: {hint}</div>}
          <Button onClick={onNext} className="mt-3 bg-black/40">Volgende</Button>
        </motion.div>
      )}
    </AnimatePresence>
  );
}

// =============================
// Minigames
// =============================
function MiniGames({store}:{store:ReturnType<typeof useStore>}){
  const [selected, setSelected] = useState("runner");
  return (
    <div className="grid lg:grid-cols-3 gap-6">
      <Card className="bg-white/10 border-white/20 lg:col-span-2">
        <CardHeader>
          <CardTitle className="flex items-center gap-2"><Swords className="w-5 h-5"/> Minigame — {selected === "runner" ? "Taalrunner" : "—"}</CardTitle>
        </CardHeader>
        <CardContent>
          {selected === "runner" && <TaalRunner store={store} />}
        </CardContent>
      </Card>
      <Card className="bg-white/10 border-white/20">
        <CardHeader>
          <CardTitle className="flex items-center gap-2"><Keyboard className="w-5 h-5"/> Besturing</CardTitle>
        </CardHeader>
        <CardContent className="space-y-2 text-sm">
          <div>⬅️/➡️ pijltjes: van baan wisselen</div>
          <div>Pak het **juist gespelde** woord. Bots niet tegen het foute woord!</div>
          <div className="text-white/80">Na elke 5 goede keuzes wordt het sneller.</div>
        </CardContent>
      </Card>
    </div>
  );
}

// Simple lane runner using requestAnimationFrame
type RunnerItem = { lane:0|1|2; y:number; good:boolean; text:string; speed:number };

function makeRunnerWord(){
  const banks = [
    { good:"hij wordt", bad:"hij word" },
    { good:"antwoordt", bad:"antwoort" },
    { good:"gefietst", bad:"gefietsd" },
    { good:"bioscoopkaartje", bad:"bioscoop kaartje" },
    { good:"dan ik", bad:"als ik" },
    { good:"gereisd", bad:"gereist" },
  ];
  return pick(banks);
}

function TaalRunner({store}:{store:ReturnType<typeof useStore>}){
  const [lane, setLane] = useState<0|1|2>(1);
  const [items, setItems] = useState<RunnerItem[]>([]);
  const [playing, setPlaying] = useState(false);
  const [score, setScore] = useState(0);
  const speedRef = useRef(1);
  const raf = useRef<number>();

  useEffect(()=>{
    const onKey=(e:KeyboardEvent)=>{
      if(e.key==='ArrowLeft') setLane(l=> (l>0? (l-1) as 0|1|2 : l));
      if(e.key==='ArrowRight') setLane(l=> (l<2? (l+1) as 0|1|2 : l));
    };
    window.addEventListener('keydown', onKey);
    return ()=> window.removeEventListener('keydown', onKey);
  },[]);

  const spawn = ()=>{
    const w = makeRunnerWord();
    const pair = shuffle([
      { lane:0 as 0|1|2, text:w.good, good:true },
      { lane:2 as 0|1|2, text:w.bad, good:false },
    ]);
    // also sometimes swap lanes to middle
    const lanes:[0|1|2,0|1|2] = shuffle([0,1,2] as [0|1|2,0|1|2,0|1|2]).slice(0,2) as any;
    const a:RunnerItem = { lane: lanes[0], y: -10, good: true, text: pair[0].text===w.good? pair[0].text : w.good, speed: speedRef.current };
    const b:RunnerItem = { lane: lanes[1], y: -30, good: false, text: pair[1].text===w.bad? pair[1].text : w.bad, speed: speedRef.current };
    setItems(s=>[...s, a, b]);
  };

  const loop = ()=>{
    setItems(prev => prev.map(it => ({...it, y: it.y + it.speed})).filter(it => it.y < 110));
    // collision
    setItems(prev => {
      const collided = prev.find(it => it.lane===lane && it.y>80 && it.y<90);
      if(collided){
        if(collided.good){ setScore(sc=>sc+1); store.award(3,0); }
        else { setScore(0); store.miss(); speedRef.current = 1; }
        return prev.filter(it => it !== collided);
      }
      return prev;
    });
    raf.current = requestAnimationFrame(loop);
  };

  useEffect(()=>{ return ()=> raf.current && cancelAnimationFrame(raf.current); },[]);

  const start=()=>{
    setScore(0); setItems([]); speedRef.current=1; setPlaying(true);
    raf.current = requestAnimationFrame(loop);
    const spawner = setInterval(()=>{ spawn(); }, 900);
    const speedUp = setInterval(()=>{ speedRef.current += 0.2; }, 5000);
    const cleanup=()=>{ clearInterval(spawner); clearInterval(speedUp); cancelAnimationFrame(raf.current!); setPlaying(false); };
    // stop after 60s
    setTimeout(cleanup, 60000);
  };

  return (
    <div className="grid md:grid-cols-[1fr,280px] gap-4">
      <div>
        <div className="relative h-[360px] rounded-2xl overflow-hidden bg-gradient-to-b from-black/30 to-black/50 border border-white/20">
          {/* lanes */}
          {[0,1,2].map(i=> (
            <div key={i} className="absolute inset-y-0" style={{left:`${i*33.333}%`, width:'33.333%'}}>
              <div className="absolute inset-0 border-l border-white/10"/>
            </div>
          ))}
          {/* player */}
          <motion.div className="absolute bottom-6 left-0 right-0 mx-auto w-24 h-10 rounded-xl bg-white/20 backdrop-blur border border-white/30"
            animate={{ x: lane===0? 'calc(-33.333% + 16px)': lane===1? 0: 'calc(33.333% - 16px)' }}
            transition={{ type:'spring', stiffness:220, damping:18 }}
          >
            <div className="text-center text-xs pt-2">Jij</div>
          </motion.div>
          {/* items */}
          {items.map((it, idx)=> (
            <div key={idx} className="absolute px-3 py-2 rounded-xl bg-black/60 border border-white/20" style={{ left: `calc(${it.lane*33.333}% + 8px)`, top: `${it.y}%`}}>
              {it.text}
            </div>
          ))}
        </div>
        <div className="mt-3 flex items-center justify-between">
          <div>Score: <span className="font-semibold">{score}</span></div>
          <div className="text-sm text-white/80">1 minuut per potje</div>
        </div>
        <div className="mt-3 flex gap-2">
          {!playing ? <Button onClick={start} className="bg-black/40">Start</Button> : <Button disabled className="bg-black/40">Bezig…</Button>}
        </div>
      </div>
      <div className="text-sm space-y-2">
        <div className="font-semibold">Lesdoelen in deze game</div>
        <ul className="list-disc pl-4 space-y-1">
          <li>Werkwoordspelling: <em>wordt/word</em>, <em>antwoordt/antwoort</em></li>
          <li>Voltooid deelwoord: <em>gefietst/gereisd</em></li>
          <li>Samenstellingen: <em>bioscoopkaartje</em></li>
          <li>Grammatica: <em>dan ik</em> (niet <em>als ik</em>)</li>
        </ul>
      </div>
    </div>
  );
}

// =============================
// Progress
// =============================
import { ResponsiveContainer, LineChart, Line, XAxis, YAxis, Tooltip } from "recharts";
function ProgressView({store}:{store:ReturnType<typeof useStore>}){
  const data = store.history.map(h=>({ name: h.day.split("/").slice(0,2).join("/"), xp: h.xp }));
  return (
    <div className="grid md:grid-cols-2 gap-6">
      <Card className="bg-white/10 border-white/20">
        <CardHeader><CardTitle className="flex items-center gap-2"><Sparkles className="w-5 h-5"/> Voortgang</CardTitle></CardHeader>
        <CardContent>
          <div className="h-44">
            <ResponsiveContainer width="100%" height="100%">
              <LineChart data={data}><XAxis dataKey="name" hide/><YAxis hide/><Tooltip/><Line type="monotone" dataKey="xp" strokeWidth={3} dot={false}/></LineChart>
            </ResponsiveContainer>
          </div>
          <div className="mt-4">
            <div className="flex items-center justify-between text-sm mb-2">
              <span>Niveau {Math.floor(store.xp/250)+1}</span>
              <span>{Math.min(100, ((store.xp%250)/250)*100).toFixed(0)}%</span>
            </div>
            <Progress value={Math.min(100, ((store.xp%250)/250)*100)} className="h-3"/>
          </div>
        </CardContent>
      </Card>

      <Card className="bg-white/10 border-white/20">
        <CardHeader><CardTitle>Dagelijkse doelen</CardTitle></CardHeader>
        <CardContent className="grid gap-3 text-sm">
          <Goal done={store.xp>=60} text="60 XP verzamelen"/>
          <Goal done={store.streak>=5} text="Streak 5 halen"/>
          <Goal done={store.coins>=10} text="10 munten verdienen"/>
        </CardContent>
      </Card>
    </div>
  );
}
function Goal({done,text}:{done:boolean,text:string}){
  return (
    <div className={`p-3 rounded-xl border ${done?"bg-emerald-500/20 border-emerald-400/40":"bg-white/10 border-white/20"}`}>
      <div className="flex items-center gap-2">{done?<CheckCircle2 className="w-4 h-4"/>:<XCircle className="w-4 h-4"/>}{text}</div>
    </div>
  );
}
