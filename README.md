<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Loja Tech2026</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --void:#060a14;
    --panel:#0c1526;
    --panel-2:#101d34;
    --line:#1c2c48;
    --blue:#2fa8f5;
    --cyan:#5eead4;
    --violet:#8b6bf5;
    --white:#f2f6fb;
    --muted:#7d8ba3;
  }
  *{box-sizing:border-box;}
  html,body{margin:0;padding:0;}
  body{
    min-height:100vh;
    background:var(--void);
    color:var(--white);
    font-family:'Inter',sans-serif;
    overflow-x:hidden;
    position:relative;
    display:flex;
    justify-content:center;
  }
  #bgcanvas{
    position:fixed;
    inset:0;
    width:100%;
    height:100%;
    z-index:0;
  }
  .glow-orb{
    position:fixed;
    border-radius:50%;
    filter:blur(90px);
    opacity:.35;
    z-index:0;
    pointer-events:none;
  }
  .glow-orb.one{
    width:520px;height:520px;
    background:radial-gradient(circle, var(--blue), transparent 70%);
    top:-180px; left:-160px;
    animation:driftA 16s ease-in-out infinite;
  }
  .glow-orb.two{
    width:480px;height:480px;
    background:radial-gradient(circle, var(--violet), transparent 70%);
    bottom:-200px; right:-160px;
    animation:driftB 19s ease-in-out infinite;
  }
  @keyframes driftA{
    0%,100%{transform:translate(0,0);}
    50%{transform:translate(40px,30px);}
  }
  @keyframes driftB{
    0%,100%{transform:translate(0,0);}
    50%{transform:translate(-30px,-40px);}
  }
  .wrap{
    position:relative;
    z-index:2;
    width:100%;
    max-width:460px;
    padding:56px 24px 60px;
    display:flex;
    flex-direction:column;
    align-items:center;
  }
  .logo-stage{
    position:relative;
    width:168px;
    height:168px;
    margin-bottom:22px;
    display:flex;
    align-items:center;
    justify-content:center;
  }
  .logo-ring-glow{
    position:absolute;
    inset:-14px;
    border-radius:50%;
    border:1px solid rgba(94,234,212,.35);
    animation:ringPulse 3.2s ease-in-out infinite;
  }
  .logo-ring-glow.delay{
    inset:-28px;
    animation-delay:.6s;
    border-color:rgba(47,168,245,.25);
  }
  @keyframes ringPulse{
    0%{transform:scale(.9); opacity:.9;}
    70%{transform:scale(1.18); opacity:0;}
    100%{opacity:0;}
  }
  .logo-img{
    position:relative;
    width:150px;
    height:150px;
    border-radius:50%;
    object-fit:cover;
    box-shadow:0 0 40px rgba(47,168,245,.45), 0 0 90px rgba(139,107,245,.25);
    background:var(--void);
    z-index:2;
  }
  .scan-sweep{
    position:absolute;
    width:150px;height:150px;
    border-radius:50%;
    overflow:hidden;
    z-index:3;
    pointer-events:none;
    mix-blend-mode:screen;
  }
  .scan-sweep::before{
    content:"";
    position:absolute;
    top:-50%; left:-50%;
    width:200%; height:200%;
    background:conic-gradient(from 0deg, transparent 0deg, rgba(94,234,212,.55) 8deg, transparent 30deg, transparent 360deg);
    animation:spin 3.6s linear infinite;
  }
  @keyframes spin{ to{ transform:rotate(360deg);} }
  .eyebrow{
    font-family:'JetBrains Mono', monospace;
    font-size:11px;
    letter-spacing:.22em;
    color:var(--cyan);
    text-transform:uppercase;
    margin-bottom:10px;
    display:flex;
    align-items:center;
    gap:8px;
  }
  .eyebrow .dot{
    width:6px;height:6px;border-radius:50%;
    background:var(--cyan);
    box-shadow:0 0 8px var(--cyan);
    animation:blink 1.6s ease-in-out infinite;
  }
  @keyframes blink{ 0%,100%{opacity:1;} 50%{opacity:.25;} }
  h1{
    font-family:'Space Grotesk', sans-serif;
    font-weight:700;
    font-size:34px;
    letter-spacing:.01em;
    margin:0 0 6px;
    text-align:center;
    background:linear-gradient(90deg, #ffffff 30%, var(--cyan) 100%);
    -webkit-background-clip:text;
    background-clip:text;
    color:transparent;
  }
  .tagline{
    font-size:14.5px;
    color:var(--muted);
    text-align:center;
    line-height:1.5;
    margin:0 0 34px;
    max-width:320px;
  }
  .tagline b{ color:var(--white); font-weight:600; }
  .rail{
    position:relative;
    width:100%;
    display:flex;
    flex-direction:column;
    gap:16px;
  }
  .rail::before{
    content:"";
    position:absolute;
    left:29px;
    top:8px;
    bottom:8px;
    width:1px;
    background:linear-gradient(to bottom, transparent, var(--line) 8%, var(--line) 92%, transparent);
    z-index:0;
  }
  .pulse-dot{
    position:absolute;
    left:26px;
    width:7px;height:7px;
    border-radius:50%;
    background:var(--cyan);
    box-shadow:0 0 10px var(--cyan), 0 0 18px var(--cyan);
    animation:travel 3.5s linear infinite;
    z-index:1;
  }
  @keyframes travel{
    0%{ top:0%; opacity:0;}
    8%{opacity:1;}
    92%{opacity:1;}
    100%{ top:100%; opacity:0;}
  }
  .node{
    position:relative;
    z-index:2;
    display:flex;
    align-items:center;
    gap:16px;
    padding:16px 18px;
    background:linear-gradient(135deg, var(--panel), var(--panel-2));
    border:1px solid var(--line);
    border-radius:14px;
    text-decoration:none;
    color:var(--white);
    transition:transform .25s ease, border-color .25s ease, box-shadow .25s ease, background .25s ease;
    overflow:hidden;
  }
  .node::after{
    content:"";
    position:absolute;
    top:0; left:-120%;
    width:60%; height:100%;
    background:linear-gradient(120deg, transparent, rgba(94,234,212,.18), transparent);
    transform:skewX(-20deg);
    transition:left .55s ease;
  }
  .node:hover::after{ left:130%; }
  .node:hover{
    transform:translateY(-3px);
    border-color:var(--cyan);
    box-shadow:0 8px 28px rgba(47,168,245,.28), 0 0 0 1px rgba(94,234,212,.25) inset;
    background:linear-gradient(135deg, #101f38, #142544);
  }
  .node:active{ transform:translateY(-1px) scale(.99); }
  .node-icon{
    flex:0 0 auto;
    width:42px; height:42px;
    border-radius:10px;
    display:flex;
    align-items:center;
    justify-content:center;
    background:rgba(47,168,245,.12);
    border:1px solid rgba(47,168,245,.3);
  }
  .node-icon svg{ width:20px; height:20px; }
  .node-text{ flex:1 1 auto; min-width:0; }
  .node-title{
    font-family:'Space Grotesk', sans-serif;
    font-weight:600;
    font-size:15.5px;
    margin:0 0 2px;
  }
  .node-sub{
    font-family:'JetBrains Mono', monospace;
    font-size:11px;
    color:var(--muted);
    letter-spacing:.03em;
    white-space:nowrap;
    overflow:hidden;
    text-overflow:ellipsis;
  }
  .node-arrow{
    flex:0 0 auto;
    color:var(--cyan);
    font-size:18px;
    transform:translateX(0);
    transition:transform .25s ease;
  }
  .node:hover .node-arrow{ transform:translateX(4px); }
  .node.featured{
    border-color:rgba(139,107,245,.45);
    background:linear-gradient(135deg, #14213a, #1a1240);
  }
  .node.featured .node-icon{
    background:rgba(139,107,245,.18);
    border-color:rgba(139,107,245,.45);
  }
  .node.featured .node-sub{ color:var(--violet); }
  .node.featured:hover{
    border-color:var(--violet);
    box-shadow:0 8px 28px rgba(139,107,245,.32), 0 0 0 1px rgba(139,107,245,.3) inset;
  }
  .badge{
    display:inline-block;
    vertical-align:middle;
    margin-left:8px;
    background:var(--cyan);
    color:#04241d;
    font-family:'JetBrains Mono', monospace;
    font-size:9.5px;
    font-weight:500;
    letter-spacing:.06em;
    padding:3px 8px;
    border-radius:20px;
    text-transform:uppercase;
    box-shadow:0 0 10px rgba(94,234,212,.5);
  }
  .node-title{ display:flex; align-items:center; }
  footer{
    margin-top:38px;
    text-align:center;
  }
  footer .status{
    font-family:'JetBrains Mono', monospace;
    font-size:10.5px;
    color:var(--muted);
    letter-spacing:.1em;
    text-transform:uppercase;
    display:flex;
    align-items:center;
    justify-content:center;
    gap:8px;
  }
  footer .status .dot{
    width:5px;height:5px;border-radius:50%;
    background:var(--cyan);
    box-shadow:0 0 6px var(--cyan);
  }
  @media (max-width:380px){
    h1{font-size:28px;}
    .node{padding:14px;}
  }
  @media (prefers-reduced-motion: reduce){
    *, *::before, *::after{
      animation-duration:.001ms !important;
      animation-iteration-count:1 !important;
      transition:none !important;
    }
  }
  a:focus-visible, .node:focus-visible{
    outline:2px solid var(--cyan);
    outline-offset:3px;
  }
</style>
</head>
<body>

<canvas id="bgcanvas"></canvas>
<div class="glow-orb one"></div>
<div class="glow-orb two"></div>

<div class="wrap">

  <div class="logo-stage">
    <div class="logo-ring-glow"></div>
    <div class="logo-ring-glow delay"></div>
    <img class="logo-img" src="data:image/jpeg;base64,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/r182Otw8ffb6VSnL52jncgqxVxi9LLpcrxl+BOr7gAoAIAAAt1Rt1cwacLHvgAAAAAACQAAek8sszMLMMLMMLMMLMMLMMTKMTKMTKMTKTEyyYWYuFmGFm8mMRRIACggAAAKCLdUbdXMGnCx74AAAAAAkAAAbeon567kPXj15447DjjsOOOw447DkDruQOu5A67kDruQOu5A67kDruQOvj5gE+PcAFBAAAAUEEi21K21zBpwse+AAAAAJAAAAAAAAQSoAAIAACgAgAkBQAQAAAFBBIAttSttcwacLHvgAAACQAAAAAAAEBUgACAAoAAIAJAAUEAAABQQSAALbUrbXMGnCx74AAAkAAAAAAABBKgAAgAAKAACJiQFABAAAAUEJAAAC21K21zBpkXRYf0FLXR6lLXQUtdBTFzFMXMUxcxTFzFMXMUxcxTFzFMXMUxcxTFzFMXMUxcxTVyFNXIU1chTVyFNXIU1chTVyFNXIU1chTVyFNm4inLiKcuIpy4inLiKcuIpy4inLiKcuIpy4inXErmB/9oADAMBAAIAAxEAACH+IIIIAAb7777qIAIIbzz776AAIIJ7z76IIAIPoIIIAIb77z7qIAAIJbz776AAIIJ7z77oIAIIMIIIIIb77z7qIAAIIbz776AAIIJbz76IIIIIasIIAIZ77z76IAAIIbzz76AAIII7zz6qIIIIb6sIAIb77z76IAIIIbzz77oAIIIbzz76IIIIb76sIIb77z77oIAIJbzz77oAAII7zz76IIIIb776sIb77z76IIAII7zz77Eo8MJ7zz77IIIa77776Nb77z77oAAIb7zznF9vPamzrz7qIIIJ77776IP77776IAAIJzz6epFMIII52qraIIIb77776IIP776oIAAIb7z7G6AAAIb/AF++0LJCCe+++6CCCD++6CACCG88+/ciACCCc3e+iCFPG++++6CCCCD+6iACCCW8++dhACCCe+g+yCCSeP8Avvugggwhq+ggAgghvPPu6IwgglvC/eggggg2Pvugggghvq4gAgghvPPvpdQggjvPkwCzgwgvQvvoggwhnvqwAgghvPPvug9QghvPO8Tctghnvjvoggghvvv6gAghvPPvugFyQjvPNW9zYgBvvvoQggwhvvv/AOMIJ7zz77oAJJx7zz74ER9b7777p8IIJ777/wD6DGe8+++6AACTJ8++6iCvd+++++x2DCO++/8A4gg3PPvvugAghnE1vuoggbdPvvvpjggnvv8A/uIIIPz776AAAILzy9PMIIJNT777oJjgI77/AP7CCDDC+++gACCCe8++FrLCCs/++6CevjG+/wD+wggwx6/voAAggjvPvsgpBDwPvvuh5Owxnvv+wggww/6/oAAgghvPvuggAkF/sxKDVcwhvvv+4ggwx/8A6ugAIIIbzz74IAIIb7787KMMIZ77/wDiCDDD/wDvqwAgghvPPvoggguPvgzqQg61E9v/APoIIMf777+IAII7zz76IIII6v7wDI8MKfTPX+IIIMf777+MIIJ7zz76IIIb76nDTVzPgHCU9voIIM/777+MMMLzz77qIIIJ77444IIAIby4/wDiCCDH++/7jDCDc8++6CCCG7//AN+4iwgxtu//AMIIIMf77/sMMIMLz77IIIIJ6zl1JOAJMT6vyLMiJ7KX7+sMIIc+r77IIIILb74Po4JCsaGv2OOLcFcUr/sMIIN/+r6IIIII7774YJwqJKwuuHzsPutG/TsMIIM//wDqCACCe+++6CCDIQwww0MMMNJQw0/7DCDH/wD/AL+oIIJ7777oIIJD64444IIIIL7773sMIMf/AP8Av+wggnvvvugggghvvv8AoIIMMN77/wD7CCDD/wD/AL/sMIJ7777oIIII777/AOiCDDW++/8A+wwgw/8A/wC/7DDCe+++6CCCCW++/wCgggw3/vvv6wggw/8A/wC/zDDDCywwwAAAAAwwwwwwwAAAAAQwwwwgAAAAQwwwwj//2gAMAwEAAgADEQAAEJIAAAAguAAAAOIAgAOAggABIggABIAgBIAAgCuAAAAgGAAAgGIAggBKAgABIggABIAgBOAAgAKgAAAAGAAAgOIAggAOAgABIggABKAgBIAAABOAgAAgGIAAgHIAggBGAggBIggABMAggKIAAAOAAgAgGAAAgFIAgABOAggAGAgABOAggDIAABOAAAgAGAAAgBOAAgBKAggAGAggBMAggHIAAAOAAAAhOAAAgFIAAgPMAggAHgzChIAggBMAAGEAAABIqAAAgDOAggGAAggQea5wcSbQgGIAAFIAAABIAgAAAHIAggHIggF9I0wABIEVQRYAACAAAABIAAgAACAAghGAAgHHmgggCAAwANVywFIAAAGAAAAgAGAAgAOAggBZGwgABIioBIAJWmAAAAGAAABKgGIAgABKAgAHwQgABIBfAMAAAFWwAAGAAAQGAuAAgABGAggA9gwABKBpZ+AAABK5gAGAAABGAAoAgABGAggAIxAABMAm9nwiiwPB9gBIAAQOIAAggABOAggAGAcwBOAg6/nhcxOIACDIAAAGAAAQwgDOAggAGAgwhMAgnL+nGD+AAAPgAAQOAAATYgPIAggAGAgAE4AgkBo4bMQAAAFRgABIAAAReAmIAgAAGAggFqSAACIANYwAAABIyAQMAAATYAAoggABGAgAAIsohCIAENoAAAHIM6xIAAQCYAAAggABIgggBAggfUQAAHAgAAEADahMAAQGQAAQSwABIggABIAgBIJogFEowAGAA3AGAAQCQAAQGAgBIggABMAgAMAFsh+wAAHAJv42IAAWQAAQHAQhIggABOAgBOAAgB2W0yJ1U4AGAAAQYAAQGAQAqggAAOAggHAAgAOAAAdAQwQOIAARYAAQPAQAAggABOAggBIAABJQBNi6QA6iQyAReAAAGAAABYwgBMAggDIAADMFAEYYEAQMLUIhYAAAWQAABYAwBIAggBIAACAAHTzUkeYs6epwOAAAcAAABYAQlAggACIAAFIAAIBAAEgOMgARcAAAWAAAWIAQAoggBGAAACBTjTy4AiCfCAQHQBCBcAAAWAAQASwgBEAAAHIETgDhIZF5SA4bdpzetSgBSAAACcAwBMAAABCAANmIskDXj8i+gecHy/tyWAQABYAAzAAABDMAADIgB2jxIuSPv6VTvqNlGAQADcAAQwAgHIAAAGAABiojjjugggj24giXOAQBeAAQFawAHIAABOAAAFsYQRTQQQIPAQQR+QQBeAAQHeAwHIAAAOAAAHGAAAeAAAXfYAAXOQABfAAQFeAA3IAABOAAAHMAABfIAATaAAAVeQQBfAAQHeAAA4AAAGAAAHKAAAeAAAXYQAAHKAABfAAQFcAABSwMc8wwwQ8wwQws8cQE88cYgs8cYgksc4ggssoP/9oACAECAAE/AEICcnf9ia/3E3b/AAv2Lr/cTdv8L9i6/wBxN2/wv2Lr/cTdv8L9i6/3E3b/AAv2Lr/cTdv8L+xJbUrgpUroBMCSeP7lz1DCpN1OVpY/KYIplFP2DX+4m7f4Xf0IKyAkFROQDDErYSl4XFXBzRhV8h7Ybs1hkVuDB5y8PvwQbQYb/eJ6E436YNuS4zqP5YFssHzyOlJhD8vMCl5tzQaV7jhiasRhfBBaPo5O4/CJqyHWammyIHnJzdIyj3b9r/cTdv8AC79JSC5g4MCRwlnIPmYalmpRNcCectWU/wBckTVu0qlofnV8B8+6HplbuFa1K6T8NxWJa0nmci7w5qsYfy6os+2mncVf1Szy8FXQc3XFp2K29VbdG3P4V/I6YdaU2opULqk5Qf6yb5r/AHE3b/C77ISRmFUyJTwlfAaTDjzcm3zQOCkZVH+ssTk8uYVVRweanMn+e5AqaDCTginls22FN0Q6byMys6PmmJ2zEzjdQQF0q2sZOg+ifZDrSm1KQoXVJNCN71/uJu3+F3xpouKSlOEqNBDbaJRnkCBVR5yv5xOTan13j+VPNG6siTxXJhQxW0quaVAZege/c2BauxqDLhxFcAnzFcn4T7DGqCRDqdlQMdsY/pI+afdvev8AcTdv8Lvlhy3CdI9FPxPwi3Jy8oNJ4KMKtKv5bqTllTDiUJz5TyJzmLQSliUcSnAAi4OvB37qxpjbTWNwm8VenkPWPbWLVk9rPLR5vCR+FXyyb1r/AHE3b/C72BXrhKBLMf8Aloqen+ZhaytRUcqjU7qxJDYW76hju4fwpzD4mNUS7rAHPWPZU7rU9NbFMJT5rwuHpyp9uDrjVTLhSG3BlbN1X4VZO4+/etf7ibt/hd7kG77zQ9IE9WGLbdusU56gOrL8N1Yshs7l5QxGsJ9JWYfEwkRb0o7MbEG0FYTeKsIGHBTLH9iTX3J70/OP7DmvuT6yfnBFPK2soUlQypIUOo1i0GtllncFQW74/LjfDetf7ibt/hd7sYVmE6Eq90W/gS0OVSvduWWi4pKUipUaCJKVEu2lCc2U85WcwBAECNUVpbCjYUHHdGN6KPmr3bmVx5Rv0pcfo3rX+4m7f4Xe7ENJhGkKHsjVGnFaPpK925sGQujZlDCrA3oTnV1+6AIAgCJuaTLNqcVkSMA5ysw6zEzMKfWpxeFSzX+XQNzLi5LI9Fkfo3rX+4m7f4Xe7PcuPNK9IDvwRbaCtivMUD8PjuU2tMJwB0imhPyj+2Zn749yflFgvOPMlbir9VkJ6B0aYEW/aW2HNjSfq2v4l51dGYblpsuKSgZVqCR0qNItVQZlHtDdwfmxR7961/uJu3+F3sGmHkhoJmpcf5qKHQr+RhxBQpSTgKSQekbqxmrksyOVN71sMW9aO127iT9Y6KD0U51fAbqwJfZJhKszOP8Am8324eqNU89VptrOtV5X4U5O8n2b1r/cTdv8Lvmp6d4TKvxI/wBw+MW9KUXsyRirwK0K/n79yhN4gcpA74U4iWavKwJaQPYMnSYnZtUy4pxXnZBzU5hurFssS0uL+KtzHWebyJ/KPbWLUm9sPLUOCMVH4U/PLvWv9xN2/wALvjLpaUlacBSa/wBaIl9jnWcOFKxRSc6VfMZonpJUq4UKyearMpPL89xZTWyTDKfTBPQnD8I1RWlsq9hQcRs4/pL+SffurBs2+pL7icRBqhJ89Qz/AIR7TGqO1whvYWzjuj6z0EcnSr9O96/3E3b/AAu+2ZaKpRdeEhXDT8R6QiaQ1PNDzknClYypP9ZRE5IOSyqKFUngrHBV8jo8snMmXUpaeFcUlB5pVgvdQr1wTubF1PKfIceBQ1lCcinPkj2nNFsTrUigXaXyKIaHJzjyJHth11TilLUbylGpO96/3E3b/C79I2guWVgxknhIzdXIYlZliebuiixTGbVwh1fERaGpy7jMKy/u1fBXz74elnGTRaFI6Rg78h3MnY0xM0utlKT568VPtwnqrErqeblqKX9cvlIxEnQPiYntUSZZJbbo65kB8xHTynR3w++t5SlrUVqVlJ/rJvmv9xN2/wAL5DvrbikEKSopUMhBoYltUSxgeTsnpjAruyH2RKWpKvJpsiQTlS5i/qwHqh+yZVxJVsKMOdGL+k0hGp+WUaXVD88I1NSg8xSulavhSFSsvLE4jbVM5p7zhh/VNLtJokl5QzJ4PrHB3Vi0LffmsWuxI5iM/SrKfYNG/a/3E3b/AAsH9hQ6pHBUpPQSPdCbQfTkfc9dUKtB9WV90/6ivnClE5TXp/YNf7ibt/hd+bVj9/lK1LNEwWlJ86GXL3T5Jg0A6Yb4IharoJhDhBG+6/3E3b/C783w+/yLyHoiWz+Rnh9/kmMg6Ya4IiYVkEOUujRDKqp3zX+4m7f4Xfr11RPTG2PRhJvDpihbOiFTFcghlu7hMP1GGFuX8FISKDogDZFRtdOmGTdURvmv9xN2/wAL9i6/3E3b/C73SKRSKeQJJzV/Zdf7ibt/hd6k5ra6rwSF4KUMSk5srLjtxI2O9g/CKxOWkZhITcSihrghcxteWZWlAWSEDD+GFW2v7hPtiy5PbLt08FIvK6OTrMTFshhZbaaRdbxT8aUi1Hpd5CHG8V08JNP1ZrwizkVkX8H3n6RFmoOzs4Dwxmi30jbAzC6mHLVZlg2iXbQ4PPJH9YxjVBKoRsTiU3C7W8nu9sXk2dKtLDaVuPUqVaRXuGSLbl0LaZmUJubJS+B6Qr3xJTsvKS95IS7MKyhQODr5oHJnicCJySMwptLbiMhGfGu+qffFhyiEtPTTidk2KtxJw4UiveTQCJq0UvMrTMyymln+5UlHdhV7dG86/wBxN2/wu92WP+jmP9T9Hkdm1S0owtKUqJCE434Ydt5xxKkbG3jgpz5+uNTawHVpzqRg6jE+0pt51KhTHUekE1BiYst1lpDyroSumCuML2TB0RYzmxSTywKlCnFUOTAkRJW848622W2xfVTBX5xqk/7x+RPxizLNQwjbUzipGFtBz8hIzk5h1mLStBU25fOKkYEJ5E/Mxb+NKyqhkxfaiLTxLOlgcqtj/STFj2QZsla8RlvhKyXqeaPic0WzaiXQGGBdZb5PPp/sHtOGLCduyLyki8pouGmkJChFlTK7QYmUP0WEDAqlKVB/TTedf7ibt/hd7lbT2FlxnY72yXsa9Sl4UyU8jNvhDaG1S4c2NIGFXJoux/b7f+Db7x/wht5TawtBuqSajR/KE6o0qpskshxaciv/ANBpFo2o5NkXsRKeCgf1hMS1q7DLuMbHe2W9j3qUvCmSnxiUf2Fxtyl7Y1BVMlaaYn7Q2y8l0t3Qm7VF6tbummfog6qQcBlQelf/ANItS1EzYQAylm5XIctfyiJG3dia2F1lMwhPBrm7wQYtS1VTik4uxob4CB/WWJLVIJdpDQlwoIFCb/C5TS7nid1QJfaW3tVLd8cO9wf4Ysq1lySlFIC0L4aDgrpBzKib1RXm1NMMJlg5wyMuHLkAy8u86/3E3b/C74BWNjVzT3Rsauae6NjVzT3Rsauae6NjVzT3Rsauae6NjVzT3Rsauae6NjVzT3Rsauae6NjVzT3Rsauae6NjVzT3RcVzT3b3r/cTdv8AC742soNRlEbec0d0bec0d0bec0d0bec0d0bec0d0bec0d0bec0d0bec0d0bec0d0bec0d0bec0d0bec0d0bec0d0GdcPJh0b3r/cTdv8L9i6/wBxN2/wv2Lr/cTdv8L9i6/3E3b/AAsMuFda5opp90U0+6KafdFNPuimn3RTT7opp90U0xTT7o64pp90U0+6KaYppjrimn3RTTFNMdcU0xTT7oppimmOuOuKafdFNMU0xTTFNMU0+6KaYppimn3RTT7o1/eJu3+Fj//aAAgBAxABPwBSq/YmvfxT23w32Lr38U9t8N9i69/FPbfDfYuvfxT23w32Lr38U9t8N9i69/FPbfDfsTsw23w3EN/iUE+8wq2pQZZtj/1UH4wi2JRfBm2CeTZUV7qwlYUKghQ5Qaj9g17+Ke2+G3999DKStxaW0JyqUQlI6zFp6vWW6plW9sK+8XVDfUOEr+GJ3VHPzmDZnBX92zVA6MXGV1kxK6nLQfN7azuN5zmJ+sgwnUTPHzW09Lg+FYd1FWgmpDSF/hcTX2kQZCekcOxvsU85N6nrJxfbErq0m5egWUzKc4cFFU0LFDXprFkaq5aeomuwOfduZCfRXkPsOjfte/intvht+tzVAzZqKrN9xQ+rZBxlaTzUae6J+0Zy2HgDedqfq2G63EdCfepXfFjagqALnF6dgbOTQtfwT60SdnMSoussoaHopwnpVlPWdzaOpyUna32QlZ/eN4i/ZgV+YGLS1IvSYKmv+obGEkCjifxJzgcqe6LI1VuSdEP1eaycriOjlSOQ9US003MIS40sOIWKhQ/rARnBwjfNe7intvht91R2+izGa4FvOVDLfKecr0E+3JElKTNtTJwla14zrquC2n4AeakdUWPYjFnIutJqsjHdPDWfgnkAwblSgkEk0CRUnkAywDXDy+XVJqUTNAvS4CHhhUjIh34Jc05DnjU/aTtmOELvbGo0dZPmkecBmcHtyGGXkuoStCryViqSM4O9693FPbfDb5NzSJZpx1w3UNJKldWYaTkGmJp5+2pzALy3lXW05m0DIPwpGEnpMWLY7dnMpaQKqyuOZ3F5z0cgzDdapbUx2ZJs4z60bNTM2VCielXu6dzqnsQOpMw0n6xAq4B56B534k+0RqVt4NOiWWfq3j9Wo5EOHN+Ff6qb3r38U9t8Nvmr+18Lcog4MDj3+xP+7ujUJZAbaM2tOO/VLdfNbGU/nPsG6tO0ESTK3l+aMVPOWeCkdJ9kWIpc5aLTjhvKU4XFflBV3CmDdaoLEMpNEoxGnfrGzzTXGSPwqyaKRY07tqXbWTVYFxz8acp/Nl69617+Ke2+G3tSgkEnAAKnoETAVak+qhwzL1E6EVoPVRDDKWUIbSKJbSEpGhIputVdsbbf2JBqzLkgci3POV0DII1FM3ppSvu2lHrUQPnutUsns0spVMZg3x+HIod2HqjUjOhLrjF4fWJvpFfORl70n2b1r38U9t8NveqCZ2CSml1oQ2pI6V4o98ah5cOzoVl2FtS+s4o9+61V2xtNnY0Gj0wCBTKhHnK6cw04c0JEakp5iU2dTzgbK7gTUE1AqTkB0R9IpP8AxCfVX/xgW/KHI+D+VX/GAa9flfaDqFoORxKknoUKGLDvy88wbpxXbisGZWIffvWvdxT23w296tlEWe6B5y2wei9X4Rrdt/WTSqZEIHeSfhuZmZRLtrdWbqG0lSjoHxOQaYtKfXOvreX55xU8xA4Keoe2phIhIhIjUxZezL2dYxGjiA+c58k5emm5mRcnHKebMH2L3rXu4p7b4be9WSL0g76Kmz/EB8Y1AKo5NJ5UIPcT89zqztjZF7UbVitmrxHnLzI6EZT6XRCRCRCREhJqmXUNIyqOE5kpzqOgRLS6WG0NoFEoFB8zpO5nfrJ92nnzSqdbm9a93FPbfDb3qgYLslNJGE7EpQ6UY3wjURN3J0JJwPtrR+YYw925VqbklEqMuklRJJKl1JOU8KPo1I/4ZPrL/wCUapJVmXmEtsthsJbBUASaqUTyk5qQkRqcsvazWyLH1jwqeVKMyek5TuXXAhKlHIhJUehIrFmNbNNNVw1cvn8uN8N617+Ke2+G3tSQoEHCFAg9Bhxg2ZOmgwyz15OlNajvTDLodQlaTVK0hSToIrurdd2WcfPIq6PyC78I1OWXtl3ZFD6pkgn0l5k9Gc7rVVaG1pUhJx3zcT+HKs9FMHXGo4F5brqk0DSQkHMVLy9wHt3Vdxr38U9t8Nvmriz7tyaSP8t2n8Cvh3RqJtkPNqllnHZxm/SbOUdKT7DuVqugk5Egk9UNNLmnrqRVbyz/ABGpJ0DLEhJplWkNJ80YTzlZyendW+8meeoKlLeI3TPyn8x9lIsWzhJS6G/OOM4eVavkKDq3rXu4p7b4bfJuVRMtONOCqHUlJ6840jKNMLknrJmstFsqvNq81aMx0hQwEdUWXaSJ1pLiMuRaM6FZx0chzjcWw9sUrMK/yyB0qxfjGpiythRs6xjujEB81v5q9261TaoBLjYGiFOK/vTzEHzfxq9gjU1JiYImCMRs4oPnLHvCffvNfJr3cU9t8NvttWOifbpgS4jC2vkPNPon+cNWhMWTMEAFKkGjrauCtPJ0cih1RZNss2g3fbNFDhtnhIPxTpGDyzsoJlKUK4F9KljnJThu9ZpXRAFOrc2rbiWQW2SFuZCrKlHzV7s8SlgqtB2+SUovVeXzuW76Z9mWGGEMoS2hN1CBRIGYb3r3cU9t8Nv1tWCzaKKLxHEjEdHCToPORo7ofs6YstY4SLvAdRwVdenODElqzSi6iaScP71Ar1qR/wAe6JSfZmReZdQ6PROEdIyjrG5mrWYl63nApQ8xOMr2ZOukW7qjfdxG/qGlc3hq0FWYaBGp+w3nkhTwLTWVNcC1jQMydJ6oZZS0kJQkJSnIB/WXfNe/intvht/caS4kpWkLSrKlQqDFq6im3iVy7mwq+7XjN9R4Sf4oTYE3J5W1VrW+0b36cI6wIXbc5LpNHlgjMvG/UCYltV06pQSVNqB/yx8IVqimleelPQhPxrEzNzs0tSNkfew8BN4j1U4Is/U9MupTsidgwYb/AAvVGHvpEnYTDFCU7MtOEKWK0PKlOQe079r38U9t8N+xOsIcwLQlwcikhXvj+yZXLtZkHlDSB8ITIMJyMND8iflASBkAHRg/YNe7intvht+UMHluhOWLwOaFpp5G4VlgCsFO+693FPbfDb8rg93kTlhzN5F5PI3lheWGxnhOWFih3zXu4p7b4bfqVEbFpg4I4UBuFqrDcJTdg4Y4IjZTC8IrvmvdxT23w32Lr3cU9t8NvVYvDlEA1i8OUReHKPIpYGUgdJp5K+Wvkyb9r3cU9t8NvVtWQm0Wg0pxbQCwu8jLgBFMObDFqWAJWdl5VL7i0v7HVZ4Sb6ynBmixdTKLOcU4l9x6+i5dXSgwg16cEM2WJ+0pxpby2UpW6sKSc4XSmHBnhvUSwFJO3XTQg0xcMao7UMhLFaP7xZDbdcxIwq/KB30iR1IqnWkvzMy7sj4vppjXQrg3irKdApSNTknOyjjrL1XJdNdjcUoHCMlwVvXFDNmMW2SLWk8NB9TXDg/vFRbixtSZooV2JWeNSJO0j5x2Rymk4MEM6npmdU65OOuMqr9WlKgQM/KQEDkFI1JTbqw+y4supYIuLOHBhFK8mCogtLtedfQp1bbMveCQk803Roqo1JPVGpuYcaemJNxZcDN4tk5RdVQ00EEGmaLRs6Znpq6tS2pVPBKVDDQcleETyjAIkA5Iz4lkuqdaXlSrDSqL1dChTNlEaoJtxbrMo2st7LQuKBoaKNAK80AEnliTspbD6FSs0l5A/vkqcqTy4qa9XId3Xya93FPbfDb3qiT/ANqyP+j/AO6fJL2QiftGcbWpSAFOrqilahdM4ODDEtqNYZcbcDzxLSkrAN2hKTXDgyRq2ZK5dpQwht3G0XkkA98WS+l2WYUkgjY0JOhSUgEHSCIlbbZmH3GEXituuNSqFBOUhQzVwYY1RywftGXbJKQ4lpJIygKWrJpif1KMsMuuB51RbQVAG7Q05cEakhSU/wBRfwi1rUcmF7TlMKlYrrgzDzgDmSPOPUIsiy0yLVwYylYXF85X/EZo1OJuTc4k5cb2L/nFlpvWlNKGQbJ+oCLYtbaouIF95zgpy3a+cfgM8WLZKmlKmHzefd5cJQFZa+mfYMEW5L355oKN1LgbFcmC8QYtKTRIPyy5eqCo4yak1oR+qtN517uKe2+G3u0LB21NMzOy3NguYlyt64q9wqilejyP6kyt515M2pouqUrFRQi8a0qFioj6KO/+IO9yv/kh2WS62W3BfSpN1QOf+cK1JFBUGZtbTasqKH23VAK7osmxmpAG7Va18JxWU6AMyYm7F2eaamdku7DcxLta3CTlrgrXkicl9nacard2RJTepWldEWdZm1GFMhy8VXiF3aUKhyVzdMJ1JXcImlAnOEUP64sqyjJlZLynr4AwilKfmMT1hbK6XmnVS7iuFdz6cBBFc/LFmWUmTCqKLi3OGs59HRE3qeL7q3S+UlRqMTggZBW9miUsJTDiHNsKXcNbpBw/xGLSsxE2kXjcUjgrGUVzHlES1iXXEuPPKfLfABrQUyZScm5ruNe7intvht8UoJFSQkDKTgEbaa+9b9dPzjbTX3rfrp+cbaa+9b9dPzjbbX3rfrp+cbaa+9b9dPzjbTX3rfrp+cbaa+9b9dPzjbTX3rfrp+cbaa+9b9dPzjbTX3rfrp+cbaa+9b9dPzjbTX3rfrp+cbaa+9b9dPzgTLZwBxBJyALSSfbvevdxT23w2+TMsiYQptYqlWWhpkw5Y+jUrzV+uY+jUrzV+uY+jUrzV+uY+jUrzV+uY+jUrzV+uY+jUrzV+uY+jUrzV+uY+jUrzV+uY+jcrzV+uY+jUrzV+uY+jUrzV+uY+jUrzV+uY+jUrzV+uYb1PSqFJUEqqkgjHNKje9e7intvhvsXXu4p7b4b7F17uKe2+G+xde7intvhoWkDddW56o6tx1bnqjq3HVHVHV5eqOqOqOqOqNe/intvho//2gAIAQEBAT8CJ/51wCd21CWiH6ChIxfCvh8XBfD4uH3Rk4o+gosLd4I/0BDguidUVUOyyesaeShyEJnCvmgwDcPmIqnykN+9oUSzB9Jp5qLJxIfCvl33Bl3xuqPVQbMa3r84/ZBobu2aHRGt3kBPtGE3jXyTrVwavij/AAhfE4mS+KvwCba2LPZNtNh3ghMmGP3OGmNJsi8KHEKPJOhfqHe+9StnV2xPZNaG7AKaI0+yH+o5KLaER+7m+SLid/QwpuJD3FQbTDuuKZoPDtxromJFsTa3YVEhmGaEd6MYXmg2lSkiIW07XfxojzTIO/fgpiefG/SMOmhxnQ9xUvPh+x2w6IkBsUUcpmVME5Y95Q4ZiGgUrKCAP1Y6Ju0LnNZtOKc4u2nb/wCDKzph7HbWprw8VG5PYHih3KaltSf08O8Gi9sCk5UQR+o6J2e+hnqekY28aIinzy00YJxbgmxBEFRuURgeKFR4Jgup7d32dK0559NFoTlOY31PSykC4x0Q4GiPQSsyYJ/SUHXtoUxB1raceCc26aHh3bJwNc/Ib0BRTszqW/qO5E16SVga12Q3qa5kJ3lTopGYpzDx3KitGXrzxw392yUDVMzO9OddFTwUxG1rifbpAKqUgapuZ3q0XUh+Z6OTj65uY3oiuxR4WqeR3XIQdZEybotONQXBx39LZ8veN88N2i03dUdHJxtU/I7Cqq0IVRew7rs2HdZXxImimImseT0kGEYrgExgYABw0Wk6r/IdJKRL7BiNie2+CMU4UNMO6WipAxUNt1oGCn4tyGc9nSyMvq21O92mcdWI7pLPiUcW4qin4dx/7tvdMky9EbotR+1rekkZfWOqdzdJUQ1cfPpJd9x7TnotNmxpw7psttXE4aJ91Yp6NjC8gDioMIQmhulwqCvhp8QXww+IL4afEF8NPiCNnEfUEeghvq0HJT22Gcu6bKGxx0TBq93n0dnS9BfPHd0M/HpzB69DKGsNqjirHeXdNl9Q+aJUTrHz6KVga51OA3oCnQR4uqbVOdeNTx6GS7MeqidV3ke6bL6p80VE6x8+hAqpSBqW5nf0M3H1rsh0Uh2Q9VF6rvI902WdjtEcUe7z6GzpepvncN3Qz0e6Lo3no5MUhNUc0Y7y7pss84jJUU+27FPQstEsAAYNi+KO8IXxR3hC+Ju8IUKfdEcG3Rt+SLE1bSU998knj0cMUaBkpx1IZz7pkX3Ygz0Wqza13S2e2sTy+Scj6w0G4dHAbee0Z6LQdsA7pYbpBwTH3gDip5l+GctvS2a3rHTOR9W2nE9JZ8K8S7BUU6+8/wAu6rOiXmU8KIqo8PVuI6SQbSH56HvuCpUWJrHV6SThatgxO0p7roJwTnXiTj3VJRdW/I6LRg1F8cN/SQG3WNGWiej3jdG4dJKw77xgNqDlaMWjbvi7sk4utZmE5t4UxUxB1TiPbooYq4DNBTcfVNzPSy0HVtzO9E02qNE1jie7JOPqXZHeq1U7A1zcwiKdDJtrECc66K4KPF1rq9JJy1eed3DRPRvoHr3dITVeYfTROylee316Gzm84lT8evMHr0krLGMf0hAU2KZiCE2vHgnOvGp7uBopSZ1o/UNE3I/W31HQQImphk8XHYia9HAlzFOShAQxQJ7wwVKmI5jOrw4d4MeWGoUrMCMM8NE3I3uczYcE5pbsPzF1fTo4EoX7TsCa0NFAnvDRUqYmDF8u8mPLDUbFKzoi7DsciVGl2xd+/FRpR0LMY9NDhOibAFLyAZtdzinBRIohipUaOYpyw71l5+mx/umuDto26I0iyJ+k5KLZ72bucERToWS737gocgB1tqYAzds0TE62HsHOKfELzU97w4zoe4qBPtd1uafsga7kU5gdvFU6RhnJfDa7nI2Y/wAQRs54wXw9+IQs7FyZZzONSmQGM3NCOiLNMh5lRZx8TZuHfcOM6H1TRMtI/UK+SZOw3caeaDwdxTdDtLSnzMNm9wUW0R9IUSZe/j/oCtE2Ye3c4rlsXxfwuXRMVyyJijMxD9RReTvJP+wlm2VLxoLHPh1cc3f3VtysOWiNENt0FuZ/n5ZGQfOOo3YBvdwCl7Dl4W9usOLv7blyGB/kw/8AqFHsWXi/RcOLdn23K0LLfJnxMO539/ls2zoESBDc6GCSNpVuS7IEUBjbou6YMMxXtaPqNEyyJcAf0wVbtnMgBr4bbo3HvSx/yzF+JO1Z+35GtvEDFSMqJWG1g9cyrXtkwTqoXWHWdh5Iz8cmuuif9irMtt94MjG8DudxCjQWx2FjtocpmCYERzD9J+Syfy0LyX4i7Yft0/h6WvxDEO5n8lRY7YV299ZoFPS/KIT2YjZ5pwummHedj/l2L8Sdqz9vyWUy/MwvNPN0E4BRn33uOJOmSfrIMM/pC/EDLseviA+Syfy0LyX4i7Yft02RLaiA3F20+qt6brGa0f4W31UpG18Jj8QrbltTHJ4RNv8AfvOx/wAuxfiTtWft+SxnUmYfmogq1wxBTxQkYHTZ7bsCGP0r8ROrHAwb8lk/loXkvxF2w/bos2X5RGY3hvPotw2KPY81Fe55aOca9ZWNLxZdhZFFNvN21Vuyuug3hvh7fTj3nY/5di/Enas/b8kGJqntd4TVQYojMa8bnBWzZbmPMVgqx2004HRZlmvmXgkUhjecfJbGDANCn5jlEZ789isiGyLHDYgvAqcs2FqXiHCaHU2UG1XTWnFWfDMODDaeAX4gfemPJo0fh2Wo10U/VsHkpufhylNYetuXx+Wxd7IW7LE0q7bknAPFOBCnIHJ4r2YH7d5WP+XYi1p30K1bMAtWzAK3gBMbPCNFlWsZTmu2wz9lBmocwKscHf8A2CMrDJrcbXyUSKyCOc4MCtW2df8A04XU4nHRBimC9rxvaVJT8OaaCDzuLeK1DK3rorjRTtow5Vpqau4N4qPFMZ7nne4qGy+4NHEqVhCDDazAK25nXRyODNmmyZnXwGni3YfRfiOW6sUftP8A67yvkcSr7sT7q+7Eq+7EomukOLdxouVxf8x3unPLt5J+QOLd2xcrin/Ed7omum+7E/IHEcUXE8f9vaKioqaKKioqfJcOB9vkp3zJRIYhi8RVNfDdsF0p11u00C10LFqmyDENNykGjVDYnPht2G6FrYWLU+LCodrd2iXgGMae6ZAhwRuHmUJiGdl4KPKMijA4qIwsJB4KQ7QeRU+Bqzs4jRZ45/orQAueuiWk2sFXbStbC3VapmTa4VbsOiTltbtO4Iuhw9hoFHlWxRUb0RRSsDXHIb1dhwRwCuw4w4FTUvqTkd2iXlGsFXbT/CD4bjTYpyWDec317mke1ap7snaZDsgp5pMQ7FcOBV04HRIQ7sOviVoRi513gNEC0NW2hFSFMRtc6tKKQ7UeRU/2Z8wrpwKkAQ/0Vodn6ppoQcE+0bzSKU0M6orgn7z5qUbdhhTTr0RyknVhjJTjbsQqWmtSN1aqZj6413Kzq3jhRWidjVKNvRBltU26jNnHYmy8Qc66okzEdsPc0j2rVPdk7TIdkE+YYw0JFVyuF4gpqYhuYQCK6Jfs2+Smu0f5/JIdoPIp7w0VOwLlMLxBMjMd1SCrQ6nrplJT6negU5MXBdG86IHUb5KN13eakOp6qf6/pohQjFNAobGwG/yVMxta7IblIdf0URwaKngmT4caUopuCHtrxHc0j2oU92TtMh2YU/2h+SRiXoYyU/BIde4HRLSYLOeNpU1CEJ1ApDtB5FT/AGZ89Eh1/RT/AFNEnK/W70UzNarYOsnOvbTolXVhtUyKPcpIUhjNTjqxCoUMxDQJjGwW/wAlTMyYuwdXRJupEGamxWGU3eE/qHy7mku0CnT/AEzpkT/TCdDhu2kArUwsGrUw8Gp28+al45gmvDimRmRhwOSECGNt0KPNth5nBOdeNTxUj2g8lPH+mdEj11PHmKE284DNAgItYcFcZg1ROsfNScxc5p3FPhMibTtUWO2EP4CJrtUi0BtcUaHBXGYNU61oaKU3oGigzAiDPBCAxprRTcyKXW+vddfmvnE9MHEcehvHH/WYaXbhVal/hPstS/wn2Wpf4T7LUv8ACfZal/hPstS/wn2Wpf4T7LUv8J9lqX+E+y1L/CfZal/hPstS/wAJ9lqX+E+y1L/CfZal/hPstS/wn2Wpf4T7LUv8J9lqX+E+y1L/AAn2Wpf4T7LUv8J9lqX+E+y1L/CfZal/hPstS/wn2Wpf4T7Iw3DeD3bLx9XvC5a3ArlrcCuWtwK5a3ArlrcCuWtwK5a3ArlrcCuWtwK5a3ArlrcCuWNwK5Y3ArljcCuWNwK5Y3ArljcCuWNwK5Y3ArljcCuWNwK5Y3ArljcCuWNwK5Y3ArljcCuWNwKiTYcCADt/4Fa5K9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2SvZK9kr2RV7JXsir2RV7Iq9kVeyKvZFXsir2RV7Iq9kVeyKvZFXsir2RV7Iq9kVeyKvZFXsir2R+yvZH7K9kfsr2R+yvZH7K9kVeyP2V7I/ZXsj9leyP2V7I/ZXsj9leyP2V7I/ZXsj9leyP2V7I/Zf/9oACAEBAgE/If8A3XJKOQOpTyW7ou7mR7WF5o3c8CnPQPYrryAj/QCbF7Oajw8MR5q9O+L+KFgGQRtFgJgCupIQPRFT8EQUULV8X932QZzoHFNZLCQQwAMLOq4VICyvaH7yjSDz9o3HKgGvz9olLibu690Kmy4t3QjZPuACnIjNHkb3AMAiSjthClZzQ0BAKBFQsHBk5qCE3m5qMkTnsHZTFIuMQoE5uSQFxAbrHzwZUGI996BQ3EDHj8lgWN6AmoA+C87Yy5h2TPmdCnTSHuNQomict5AUbkq8hTsAdiNAREkca/4JQeaCECuSMBuSJBiU3jeBSAHJkn2YzDdhZOJh4BtCiCZTwi4/u/xP0QwVyRWJwUcFKq8bvaNxMvlOos8eVhtWgx5RponJ2EQxmDyhACODJBNQmuKMYDGbdrIDfIAABABQQeFiiESYkz2hhjEQwAICBsn7sJlxuQVo3GDLfuwB4Xpme9QZoAB0Y7LoG0IQAiSgDGMkI2QC0RRMr3fshiSiCGKujBhlTdbE94bG4kYsm1hhDmGzrB2bIkLk0jOE5HdcfzLomBNyPjcMtoINZ4BSmgsYRtB3G8cEMrQydimTbpx4MsKgUCT2tCrxC3iZtpdALjMJxTqaB/W6crR5WP3AOdpCrzG0mBNyet5bTCYOsLHr6bnunDcyZZFhs4hRJkNlJ4m0wAgSGR/nFfGK+cV8YoASWhghYkAu1dgJ6mBTMuO6c/EIpx49nBuPJF+xZORPRdschBuSaeLdVQDkjcuLZGDiiwQAAEANgEhzoLyjGiEtib53ctSu3SS0pyQNmtiQgBElBCMYsdgSyhAux72Qtm9xWlXHdMJxCKaeLYwb7k37GLV7gNnnEPzTzx7pzdYZpjsRlIBqrRlaIrVFNgHTj+BmaSxKNPRbPDoFwSG6cLwWZogdrELn4+7Z2eLAdI2N3svunFQChjKAsebW6SLYRu8htDUQWGZRIJxFBb3uqKZl0TAg1RLnMMtoxG8TYIsoI5jrLAbRhH2CGdkBKMQmT7qZXuTY3AuZNpkAsileYnaceLggZJmGcRyG6wWQwE3BQiFIGRjsqsNli0CBgBcpBdhEvG/ZgOmp7z0QxJSEUUjWWW7G17pAAOJFBgYZ8IhMYEbHIseSEQoAEchSoMNoaFg5jfYyKh0G7mD8RNfhZGAjR52L1yCdOQGg2kUwmG/BDEAGARFWkvKISITu45giBCC2YTBfjYYOHH0bAdzjgRCJMSdndAZlBAmAR2ZgE4EAkuG8BIzEK7gzsBfiNBRAgYin6IAFJNn/AHVKGgMAiIjAIq0hkN5DR3BA/wChknEPgagJqNNhvO2Ouj2TH4EK5T+chUqPIBLegEiIgUZsYc3FBXABuTOosBieiiQZE+SLCQRsGdT1AvMAoweQSUEABgnTp4UI2K5O9zrtYUKhmcQYuQIwRwUncwUpBylEaHMKi6vpVo+KF08/SNQ4BCxLohSYcHPVCxsqGAEMYcMe99kouCnJQIHig6K8Hg/ilYcj+sIESuiIRPRVucTAKYsFwh/oAKQsvLN+6Av59ES08gif+Qph2uy6mBJ/4JWKQtdgCjjoIeI+I/nH+qR5OCEjGZGjNAAaBrohZgpSWi5PY3YHQKH8u4/EePVAjGAsL7Z4QOZA4nAByXcnmgDiwxJ6HenQlaXH8GEzMAZmCDREBzqSaLSgYi64JPipsGX5ZDP5sWZR7whCAL4VPGIOFPzPT7WcQYaLkdEmZzigVQnAiOqKQoEmPDefRlaXH8CAIcRngsVg8giEYk7mbAWiKI5GZ7CGyqjn+Z6faxSG1TgjE9HFihgKb516puQ0Ln/W8+jK0uP4zOzmFgwuYT/VByNpTVA6rAA/M9Psho4HgoRISEB2TugSRVA+AHMCaYTyBzt0ceG8+jK0uP4OBmHkR4XAKNrNZBzWhdYdaSCUNBS8iXZ7IAroDyAgzQjAydRCNgQ4YzVBMTNV0FhiFwgEApDnY3iJcFNRKCgA5gtF9oamjRhjxRSUWWYIRSNZsSl03kQn0KlLMYr4YXwwjAAAKFhGOdxO8ekKAxo8eMycg95rp3gl5A5BNi8CwzlwslggoKMMiGA5Lt3H5omBZglyONyiwkFEnQQHFAU0IcapoC4251tGaMLj/wAID139W8hBAHEr7RfaK+0USYk52xghYFkBhoOdR/PS/wCDDkSvBZEBiUXPRTckk42AsvtFEvbICGRZTQjmf+euNE64p1xTrjY65OuKdcU642gOvvPw4UsZMbW/ABNNi25hoDimizhDQMgEwIVIC04RBaaGkiHQM6Is4S4steEc2465GabaAE1yhIDTQSYU3KQhRBTWiQgvB0BNAMCwBjDoFCAMiAdBAnYxkFEnLoI6EyHhIohkIj74pricgyNQgNcEVRCIMwprBRmcDxTgwHgpDHUCAeAqggAmxkjMkzchjTCjc3eLtLe9RjBGAoV8YogmDgbACqiRSJw7zZEdKHBSShaFkAJaij5BUcgjJYIcO4FskwBkQwLyQcnFOFYI+SN25OWcYlFIuLckV5gWYY805Ccd0ysIAMyBzmZ0QmquVHPwRjiYxBiiYAnEQhhhvMM25u8XaW9ymIwUNgHdikLOl/pMOZF4bJJsUw/CbYeiaEcniFnQF1ld8uysbhmbkyJARvFEsDIp+fwiKXGhEmiWBRwIr5jc3crsLe7XRj8MSsJRGAxbjY9qiLwE5cmEXpYjolu79koGTyhBMLoiESOTZlQMmdi/NZsErIsEE1ugV2gBmIpICl+dmRBCM1oxQOxNwiZy/wBtzG3HQzHBlW0IjATqiLivK0QR+MoWrybKJSXqBC5MvSIsCUDIBFEPKOaMSdEz15BLRExYbRwghmEgxT7SIOgDAiGKIuQZvLI/xAqG8gxrSDcUXABidNMM7MBHMlMl0ZGQ5dAiExcOC+IE0MMDIhgiYiE3iQKiTUgCiCM7zbne1069Ob05vtBaSJfYfw9r2OU5vTm+2QEOKJedjpynKe0mq5/7nPDIHX0y+mX0y+mX0y+mX0y+mX0y+mX0y+mX0y+mX0y+mX0y+mX0y+mX0S+mX0S+mX0y+mX0yGuEMRu0D3C9y0o9rSj2tKPa0o9rSj2tKPa0o9rSj2tKPa0o9rSj2taPa1o9rWj2taPa1o9rWj2taPa1o9rWj2tSPa1I9rUj2tSPa1I9rWj2tSPacoAaLe//AAVde6e1mdPazOntZnT2szp7WZ09rM6e1mdPazOntZnT2szp7WZ09rM6e1mdPazOntZnT2szp7WZ09rM6e1mdPazOntZnT2szp7WZ09rM6e1mdPazOntZnT2szp7WZ09rM6e1mdPazOntZ3T2s7p7Wo3tZ3T2tRva1G9rUb2tRva1G9rUb2tRva1G9rUb2tRva1G9rUb2tRva1G9rUb2tRva1G9rUb2tRva1P6Wp/S1P6Wp/S1P6Wo3tan9LU/pan9LU/pan9LU/pan9LU/pan9LU/pan9L/2gAIAQECAT8QoDcbf+2hxilxC6LvdPxKo9HIkP4tAB8oPIyi3BeQWqvLx/oGfDgQZlDqm4M1BQ6FBhDfPafBBQDi4CC2Sx+4gAU8sCaHWYn4lNQYHuom8n8vRENvp0kKlDOTpKAOFeKEBRIAALAJgtyDymoaT4HNirU4+MDyjvJULoJOOG8ErRmoE51kPhcjoucmKQmBDFByQ/cKHijwTFOIG9w4AGAAESVFVP0DgoPAgBgmgOYAJ9bWUOMifwC0+hECSmpE7AFIWR0MnWFN3GRxiYQ7WITogGBiFAFPhPxHlGxwuWIHehqJLABARBKnke1jxzRF6RogVErPmqp7UFbtHizCgTlaUEHBxF0cguzC8FQMfQ5ZG47yOvP5YlAcAL/IYIllC/Im5N5RyZTki5/wXcdC2CFFFcEIPkViCj6I3JxY7wLQLAAVJQWEBv2hEgCMkcluAg6oJeJi+zD+5WyvKia7gfL9iQckf2xJvsdApnU+WIUcM46SN+72a/RQIEqQyKLmKJfaTnETRBwXk7BgOIysCFQDchcUfkImogUWYUQBw3acAqmVOKEkwAAuAQDlgEAg6ZJcjUnaMPrGApxVAkmcNkcMZRtAFNRMUzygAVo4JbsIYCJJhxQBwrWcgjXOhHJF6mYLiW0Ak4AAvJRWCoYmnBZBhy2RzBGJODcQgFFIHiJcSFa7ANQUaYuDvOPRut8g/MhJM223EYRoTzOCKhX+zDnk8ojI8CixvApm38G5HvusbUz58EkMqWAknginLgmMAS2gS5ouYUEBhAEVgCc9o/R+aycxFSDD80jwKPChBcDukoyJBzFBE0XREfGhuM9oA6psn7IRsctAxw2hjegPEdkKBXCAM5dW6WcZG+w2pncbaVcQJ6ITNAUsw4E8ljuOu0uNCOUboUC8b1ianlEOx3TrJFElgFobMSLMHFUgUfMKKKI05AbnCLJMw/gQAgBgAcl1EFsJECR2r+wWTTnfggr5IPAt53S1cByRMEY5XubPCJAdJ0bCbCiiis2zFPZsY5/oMtATR8bpIBUQznZY/dzZHcOhlOKAmxAAFAEUUUUUUVQsNyhFmdCTnscog60D6iNGe6IUkWe7Jo3dzYgCcAACpKI0dTKcEbDaUUICSWAiSilL1m/ZM5HUbL4z3Q/cSc0Dgi9FMU72xrUWA8XgRRRRRRRRVNVGNMdmxNI6yieYbyjuhvF3KxhBobAICYwR9l9j3X0fdfZ9k07NEDAOaNhRI5IOQEeB3H82QCwOvIIwzmLml/G6XeS0TxlYyCJCbKW1zbnnBFFEtFRkit3Ds6suDlE6BANwWI0fCA87pKBgeSFRjgV0R2goOE9rDynuiihkLBIYkyiXjs++dHpHdTwJsC4Q5z6t1P5pTikhR0BIPFHIGBTmS2l+HDEUTRgv/EeWaDkDaMcbmlPAMF4HWCA4lRmiS4ndUem6lJO6LFT+xswHWF3Uiis+zGiG0iwOQXNwcSpI+ifPE0157brIQIgREIzjw/KRQf3MIZoPUz3hS2WFE6piJAAglBUG68o5ki5iJ2ZCAESYAIbZXO3AiEsEkcApTBMNwSG7ClFRPKECOBwbwU6BnG+QiE4Yg0I2PH9Rd3Qk5Krca62gyIxhNDsFkWKhigp5buKK9lRYpWS64FLYZK4zKxTBip2gQIEj1CHyDAAFwR4ESNJKqJI7JJz3cQty4IvCBjgD0CIeE3UYqh7oQ37ujzyT4I6ThycTs9OnQYrQcUSgzg3zwGKOqQ0kTXeBaR7qYwH/AGGCKg6mSMm4ohA5iQY/okzAgueezPAZnNLJwQAQzABATLR6Jf8Ac47yJRLgR5QAcDEQZY/RSgkuSAAe0cOABfkptg0pqaMyoE5jeKqAzhKmCMGHMMAnkXBQzx3odBCCRECFEDLFLyQrJkSdUWd6ID0DE4ydk5gCr9iNEtFCG2AKSJTc4NYU1ueVxGZTAGKAyYz0UNeD1z4RkvKDADe73V6fMCLDqwuNOKDjVIk4TBYoU2VB6qMlOFyLp2cweV0BMjFqdkhekRPjEUezj3ZAATXOOQI9VNcFe4cU/Ilk6Atsc8TIIw5iSMd9ndgwuWZQUGAMZzQ6hTHCB3eyAuHvAVUbKbHRAwGvLJ0iBU6TiiIER8yfZOwPl731/wBAMOQrwWUrWbHcq8Oak2JquVycvWu0gjsBahEvP/BAdATPvDpid6NHSA7l/lgEA20iQKC5zBJHAZMxmXAFLsMZHpRc8QknUdg/mc06AnQr6g+2KJNoV3HuJDn/AEEAiShFrF3vIxM4701S9db/ABim51IDuh9gKzgUR7BUnwQfVnEJ8E4Me8AOAAgMGTMXmgHVRMvMUYCERo4gYhdVBlTl+NDifxmLYz1qI/F47FBHeHLYPCkEd0AYMSY7z1y9db/FsMtspPdfVfj4RFyQScSwxgjEnBuIkq4SYkMTBGzVV+NDibcgEwESVB0PHk5MTNMSmhBkXJ+ECGHgkOp4b5O7jvPXL11v8QPCz3OIwSYHMoRIYJfiC0aTEvkdBAF4vj+NDibUlhJbqceaIcOFuVECBGI83KCd0moBdJRjxXEEQoDlvM1y9db/ABkTqxc5HEIaYEtRxEcDBRmyAFMyu+ljabqB541VUekDgaAP0mynhyQTYiemSUdi5ngHgAiR4RXgM03UZ0omCYogFklazWhEoUUTROqg4sXEoRABYCSJQDoPEKMXYocNdzB8SG8gobMxRFywqHctHHlolgAOljdnUQJ7o3oKmtJuZByVSUP6pkTDXoQngE+3wibnfYaBgnFpjimmUNAqsQxC0HnA6Gi0FUBlGaKi4ODyHAIED55EyL+AORmyLmuFcTe84WAsXuQTZmqNA8WFMnFxvn3Bw3kIYgoBDutWeVq7ytXeUVczeRJ62nmUqTsTIjuf1RdwGp+78CA4kQXRcKQnunolUiT1sIQILESIgVq7yiESS5MybR7C7idhQNh9xCOp/wCeiQI8F8wr5hXzCiGnBAkiPBfMK+QV8g2kJgCTcIpkPBv/AIIhrACZB0ZghwsBGQdEUwRwtezsWvb8SQjkPwATKKIInD8ExFi17bmcyQuGoHyZAd2RfNkwdlpPRF0IIcg2EniIGqMwzMDuy1HohU7McGSnZlBtdXL2pZBJOeJVH2aSRBKodud4QE2aH2gsAJBDiSOxKYAFbGGAHTDp1lGSAIhACJJYZlAsjO8FAuG4ZuTIDuGKHBOGMwgkx5dLJPOrgPSpAUcZmQkmKQRiE+h8SQrcOKzkMASfKDunAkA48ppBmJIzDTLJHMAckwF5KOmYdoc1lrePSg/RgyjUbm1mCPUvtLmdyHQpoIJLS3hD3AXkAsaVGecKIpEMghxXTppIxnupRKYyI7tetQuQGAlIAeq014T5COmQR9BDOcRDnQGNOENDTGGaOjQgBUxjmhjsxHmIwC8FgEeQ5I8qCGAwbyo9UGpwcxyTdMOMvGpTRPykX9LGJjJghiA4cXZ1IT8rQq0ZC1Si8hgjjgYNzNoMEWhfafM7keT6TLPE9SBOxkGSHRL/AONIuRkGCAZDmVjYbhmRdKwB4J5FJk7k6SGxayPXUWi3o49UrcCe2AvKbIgFxVejlG6O7itLvQNXkYYqcWYvOTppICIcQHc2qwR6F9pc7uWk3fgLjTsKIzQtk8w6AdTaS4ok3Gh14NHWkXItTWzvkfTsCQ5VP3KF8CAu3lEoHuSbAmYjgjnKn3EZxBABpEN5BHqgORmNKhTTDORJ4iooDId2wN7DqMfCCEZcZCaMFMazdYFPKZncoDyQBehRBsGXAvtDpMeYBVGJVqB+61Hsm5uEEAyBjJyrlguXtQCgSLjMli+D6WTLF1DHsRvHQjmhmEAKsKIGFXZF9g3iEWcE1oJkQULtQDxQYDAMIKJ4PTAZTMqQAAxoDSZ0fLpPQxERJCQTDgnuM9gcEQhyizKGMNg5Gh0+kqYJIWUmAs52ulgjlMUExCB2RasyvCqe13gMk4AyEgLv81tiIImannaDFTzWI5rGc1jOdjIhORBvEEAYmFxN5tBZEjU2AkSgiRqUCyxjzWM5rGc7QzArgQ8ohORJvMbAQqVjHmsY80SMy9gJERBAmJxcSI7/AO5mmNXE7FqDwtQeFoDwtAeFqDwtQeFqDwtQeFqDwtQeFoDwtAeFoDwtAeFoDwtAeFoDwtAeFoDwtAeFojwtAeFojwtAeFoDwtAeFoDwmMdUoG7WOBrY/UhfLX8Nfw1/DX8Nfw1/DX8Nfw1/DX8Nfy1/LX8tfy1/LX8tfy1/LX8tfz1/OX89fzl/PX8tfzl4BUEHyL/wV+3vPve5znve973ve973ve973ve973vc7xvWta1rWta1rWv/AAFrWtaUpSlaUpSlyl1kpdbKc//+AAMA/9k=" alt="Loja Tech2026 logo">
    <div class="scan-sweep"></div>
  </div>

  <div class="eyebrow"><span class="dot"></span>LOJA_TECH2026 // ONLINE</div>
  <h1>LOJA TECH2026</h1>
  <p class="tagline">Tecnologia que <b>acompanha o seu ritmo.</b><br>Escolha um link abaixo e garanta o seu.</p>

  <div class="rail">
    <div class="pulse-dot" style="animation-delay:0s;"></div>
    <div class="pulse-dot" style="animation-delay:.9s;"></div>
    <div class="pulse-dot" style="animation-delay:1.8s;"></div>
    <div class="pulse-dot" style="animation-delay:2.7s;"></div>
    <div class="pulse-dot" style="animation-delay:3.4s;"></div>

    <a class="node featured" href="https://collshp.com/lojatech2026?view=storefront" target="_blank" rel="noopener">
      <span class="node-icon">
        <svg viewBox="0 0 24 24" fill="none"><path d="M6 8h12l-1 12H7L6 8Z" stroke="#8b6bf5" stroke-width="1.6" stroke-linejoin="round"/><path d="M9 8V6a3 3 0 0 1 6 0v2" stroke="#8b6bf5" stroke-width="1.6"/></svg>
      </span>
      <span class="node-text">
        <p class="node-title">Loja na Shopee <span class="badge">Ofertas</span></p>
        <p class="node-sub">collshp.com/lojatech2026</p>
      </span>
      <span class="node-arrow">→</span>
    </a>

    <a class="node" href="https://www.instagram.com/loja_tech2026?igsh=MTZvb3UzbTQyMHozNA%3D%3D&utm_source=qr" target="_blank" rel="noopener">
      <span class="node-icon">
        <svg viewBox="0 0 24 24" fill="none"><rect x="3.5" y="3.5" width="17" height="17" rx="5" stroke="#2fa8f5" stroke-width="1.6"/><circle cx="12" cy="12" r="4" stroke="#2fa8f5" stroke-width="1.6"/><circle cx="17.2" cy="6.8" r="1.1" fill="#2fa8f5"/></svg>
      </span>
      <span class="node-text">
        <p class="node-title">Instagram</p>
        <p class="node-sub">@loja_tech2026</p>
      </span>
      <span class="node-arrow">→</span>
    </a>

    <a class="node" href="https://www.tiktok.com/@lojatech2026_?_r=1&_t=ZS-97qUJLQcfK9" target="_blank" rel="noopener">
      <span class="node-icon">
        <svg viewBox="0 0 24 24" fill="none"><path d="M14 4v9.6a3.6 3.6 0 1 1-3.4-4.5" stroke="#2fa8f5" stroke-width="1.6" stroke-linecap="round"/><path d="M14 4c.3 2 1.8 3.5 4 3.8" stroke="#2fa8f5" stroke-width="1.6" stroke-linecap="round"/></svg>
      </span>
      <span class="node-text">
        <p class="node-title">TikTok</p>
        <p class="node-sub">@lojatech2026_</p>
      </span>
      <span class="node-arrow">→</span>
    </a>

    <a class="node" href="https://k.kwai.com/u/@Loja_Tech2026/CzZZWE0Y" target="_blank" rel="noopener">
      <span class="node-icon">
        <svg viewBox="0 0 24 24" fill="none"><path d="M12 3 4 14h6l-1 7 9-12h-6l1-6Z" stroke="#2fa8f5" stroke-width="1.5" stroke-linejoin="round"/></svg>
      </span>
      <span class="node-text">
        <p class="node-title">Kwai</p>
        <p class="node-sub">@Loja_Tech2026</p>
      </span>
      <span class="node-arrow">→</span>
    </a>

    <a class="node" href="https://t.me/LojaTech2026" target="_blank" rel="noopener">
      <span class="node-icon">
        <svg viewBox="0 0 24 24" fill="none"><path d="M3 12.5 20 5l-3 15-5.2-4-2.5 2.3-.4-3.9L3 12.5Z" stroke="#2fa8f5" stroke-width="1.5" stroke-linejoin="round"/></svg>
      </span>
      <span class="node-text">
        <p class="node-title">Telegram</p>
        <p class="node-sub">t.me/LojaTech2026</p>
      </span>
      <span class="node-arrow">→</span>
    </a>
  </div>

  <footer>
    <p class="status"><span class="dot"></span>Conexão segura • novidades toda semana</p>
  </footer>
</div>

<script>
  const canvas = document.getElementById('bgcanvas');
  const ctx = canvas.getContext('2d');
  let w, h, nodes = [];

  function resize(){
    w = canvas.width = window.innerWidth;
    h = canvas.height = window.innerHeight;
    const count = Math.max(18, Math.floor((w*h)/42000));
    nodes = Array.from({length:count}, () => ({
      x: Math.random()*w,
      y: Math.random()*h,
      vx: (Math.random()-.5)*0.18,
      vy: (Math.random()-.5)*0.18
    }));
  }
  window.addEventListener('resize', resize);
  resize();

  function step(){
    ctx.clearRect(0,0,w,h);
    ctx.fillStyle = '#060a14';
    ctx.fillRect(0,0,w,h);

    for(const n of nodes){
      n.x += n.vx; n.y += n.vy;
      if(n.x < 0 || n.x > w) n.vx *= -1;
      if(n.y < 0 || n.y > h) n.vy *= -1;
    }

    for(let i=0;i<nodes.length;i++){
      for(let j=i+1;j<nodes.length;j++){
        const a = nodes[i], b = nodes[j];
        const dx = a.x-b.x, dy = a.y-b.y;
        const dist = Math.sqrt(dx*dx+dy*dy);
        if(dist < 160){
          ctx.strokeStyle = `rgba(47,168,245,${(1-dist/160)*0.16})`;
          ctx.lineWidth = 1;
          ctx.beginPath();
          ctx.moveTo(a.x,a.y);
          ctx.lineTo(b.x,b.y);
          ctx.stroke();
        }
      }
    }
    for(const n of nodes){
      ctx.fillStyle = 'rgba(94,234,212,0.55)';
      ctx.beginPath();
      ctx.arc(n.x, n.y, 1.4, 0, Math.PI*2);
      ctx.fill();
    }
    requestAnimationFrame(step);
  }
  step();
</script>

</body>
</html>
