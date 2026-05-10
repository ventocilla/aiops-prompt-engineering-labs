# Model Output

## Model
Claude Sonnet 4

## Why this model
Chosen for structured FinOps analysis, executive reporting and prioritization of cloud cost optimization actions.

## Output Format Note
The model returned the answer as an HTML-based visual report. The relevant report content is preserved below as the real model output.

## Generated Report

```html
<h2 class="sr-only">Hill Valley Tech AWS cost optimization report. Total monthly bill: $41,800. Identified savings: $9,200–$14,100/month, exceeding the 15% quarterly reduction target.</h2>

<style>
*{box-sizing:border-box;margin:0;padding:0}
.r{padding:1.5rem 0;font-family:var(--font-sans)}
.lbl{font-size:11px;font-weight:500;letter-spacing:.08em;text-transform:uppercase;color:var(--color-text-tertiary);margin-bottom:.6rem}
.sec{margin-bottom:2rem}
.card{background:var(--color-background-primary);border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:1rem 1.25rem}
.mgrid{display:grid;grid-template-columns:repeat(auto-fit,minmax(120px,1fr));gap:10px;margin-bottom:1.5rem}
.met{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:.8rem 1rem}
.met-lbl{font-size:12px;color:var(--color-text-secondary);margin-bottom:3px}
.met-val{font-size:21px;font-weight:500;color:var(--color-text-primary)}
.met-sub{font-size:11px;color:var(--color-text-tertiary);margin-top:2px}
.met-val.g{color:#3B6D11}.met-val.r{color:#A32D2D}.met-val.a{color:#854F0B}
hr.div{border:none;border-top:.5px solid var(--color-border-tertiary);margin:1.5rem 0}
.opp{border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);margin-bottom:8px;overflow:hidden}
.opp-h{display:flex;align-items:center;gap:8px;padding:.8rem 1rem;cursor:pointer}
.opp-h:hover{background:var(--color-background-secondary)}
.badge{font-size:11px;font-weight:500;padding:3px 8px;border-radius:var(--border-radius-md);white-space:nowrap}
.p1{background:#FCEBEB;color:#791F1F}
.p2{background:#FAEEDA;color:#633806}
.p3{background:#E6F1FB;color:#0C447C}
.p4{background:#EAF3DE;color:#27500A}
.eff-low{background:#E1F5EE;color:#085041}
.eff-med{background:#FAEEDA;color:#633806}
.eff-hi{background:#FAECE7;color:#712B13}
.opp-title{font-size:13px;font-weight:500;color:var(--color-text-primary);flex:1}
.opp-save{font-size:12px;color:var(--color-text-secondary);white-space:nowrap;margin-left:auto}
.chev{font-size:13px;color:var(--color-text-tertiary);transition:transform .18s;flex-shrink:0}
.chev.open{transform:rotate(180deg)}
.opp-b{padding:0 1rem .9rem;border-top:.5px solid var(--color-border-tertiary);display:none}
.opp-b.vis{display:block}
.dg{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:.6rem}
.dc{background:var(--color-background-secondary);border-radius:var(--border-radius-md);padding:.45rem .7rem;font-size:12px;color:var(--color-text-secondary)}
.dc strong{display:block;font-size:11px;font-weight:500;color:var(--color-text-primary);margin-bottom:2px}
.hl{background:var(--color-background-info);border:.5px solid var(--color-border-info);border-radius:var(--border-radius-md);padding:.55rem .8rem;font-size:12px;color:var(--color-text-info);margin-top:.65rem;line-height:1.55}
.txt{font-size:13px;color:var(--color-text-secondary);line-height:1.7;padding-top:.65rem}
.srow{display:flex;align-items:center;gap:8px;margin-bottom:7px;font-size:12px}
.slbl{width:155px;color:var(--color-text-secondary);flex-shrink:0;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.sbg{flex:1;background:var(--color-background-secondary);border-radius:3px;height:7px;overflow:hidden}
.sbar{height:100%;border-radius:3px}
.sval{width:70px;text-align:right;font-weight:500;color:var(--color-text-primary);flex-shrink:0}
.rgrid{display:grid;grid-template-columns:repeat(auto-fit,minmax(175px,1fr));gap:10px}
.rc{border:.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);padding:.8rem 1rem}
.rl{font-size:10px;font-weight:500;letter-spacing:.07em;text-transform:uppercase;margin-bottom:3px}
.rl.h{color:#A32D2D}.rl.m{color:#854F0B}.rl.l{color:#3B6D11}
.rt{font-size:13px;font-weight:500;color:var(--color-text-primary);margin-bottom:3px}
.rd{font-size:12px;color:var(--color-text-secondary);line-height:1.5}
.tl{display:flex;flex-direction:column;gap:0}
.tp{display:flex;gap:0}
.tline{display:flex;flex-direction:column;align-items:center;width:28px;flex-shrink:0}
.tdot{width:9px;height:9px;border-radius:50%;flex-shrink:0;margin-top:4px}
.tv{flex:1;width:1px;background:var(--color-border-tertiary);margin-top:4px}
.tc{padding-bottom:1.1rem;flex:1;padding-left:10px}
.tpl{font-size:11px;font-weight:500;text-transform:uppercase;letter-spacing:.07em;margin-bottom:4px}
.tpl.now{color:#A32D2D}.tpl.mid{color:#854F0B}.tpl.lat{color:#185FA5}
.tdot.now{background:#A32D2D}.tdot.mid{background:#854F0B}.tdot.lat{background:#185FA5}
.tl-items{list-style:none;font-size:12px;color:var(--color-text-secondary);line-height:1.8}
.tl-items li::before{content:"→ ";color:var(--color-text-tertiary)}
.concl{background:var(--color-background-secondary);border-radius:var(--border-radius-lg);border-left:3px solid #185FA5;padding:1rem 1.25rem;font-size:13px;color:var(--color-text-secondary);line-height:1.75;border-radius:0}
.concl strong{color:var(--color-text-primary);font-weight:500}
.cat-bar{display:flex;height:10px;border-radius:5px;overflow:hidden;margin-bottom:.5rem;width:100%}
</style>

<div class="r">

<div class="sec">
  <div class="lbl">Cloud cost optimization · Hill Valley Tech · May 2026</div>
  <div style="font-size:22px;font-weight:500;color:var(--color-text-primary);margin-bottom:.2rem">AWS cost optimization report</div>
  <div style="font-size:13px;color:var(--color-text-secondary);margin-bottom:1.25rem">Prepared for Goldie Wilson, CEO · 12 services · Target: ≥15% reduction in Q3</div>
  <div class="mgrid">
    <div class="met"><div class="met-lbl">Total monthly bill</div><div class="met-val">$41,800</div><div class="met-sub">Across 12 services</div></div>
    <div class="met"><div class="met-lbl">Identified savings (low)</div><div class="met-val g">$9,200</div><div class="met-sub">22% of bill</div></div>
    <div class="met"><div class="met-lbl">Identified savings (high)</div><div class="met-val g">$14,100</div><div class="met-sub">34% of bill</div></div>
    <div class="met"><div class="met-lbl">15% target</div><div class="met-val g">$6,270</div><div class="met-sub">Achievable in Q3</div></div>
    <div class="met"><div class="met-lbl">EC2 on-demand util.</div><div class="met-val r">45%</div><div class="met-sub">$8,200/mo wasted</div></div>
    <div class="met"><div class="met-lbl">ElastiCache util.</div><div class="met-val r">40%</div><div class="met-sub">Overprovisioned</div></div>
  </div>

  <div style="font-size:12px;color:var(--color-text-secondary);margin-bottom:6px;font-weight:500">Spend by category</div>
  <div class="cat-bar">
    <div style="width:48%;background:#185FA5;" title="Compute 48%"></div>
    <div style="width:24%;background:#3B6D11;" title="Databases 24%"></div>
    <div style="width:11%;background:#888780;" title="Storage 11%"></div>
    <div style="width:9%;background:#854F0B;" title="Observability 9%"></div>
    <div style="width:7%;background:#A32D2D;" title="Network 7%"></div>
  </div>
  <div style="display:flex;flex-wrap:wrap;gap:12px;font-size:11px;color:var(--color-text-secondary)">
    <span><span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:#185FA5;margin-right:4px"></span>Compute 48% · $20,000</span>
    <span><span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:#3B6D11;margin-right:4px"></span>Databases 24% · $10,300</span>
    <span><span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:#888780;margin-right:4px"></span>Storage 11% · $4,700</span>
    <span><span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:#854F0B;margin-right:4px"></span>Observability 9% · $3,700</span>
    <span><span style="display:inline-block;width:9px;height:9px;border-radius:2px;background:#A32D2D;margin-right:4px"></span>Network 7% · $3,100</span>
  </div>
</div>

<hr class="div">

<div class="sec">
  <div class="lbl">Executive summary</div>
  <div class="card txt">
    Hill Valley Tech's AWS bill of <strong style="color:var(--color-text-primary)">$41,800/month</strong> carries <strong style="color:var(--color-text-primary)">$9,200–$14,100 in recoverable savings</strong> — well above the 15% quarterly target of $6,270. The three largest opportunities are: (1) converting EC2 on-demand instances running at 45% utilization to Reserved Instances or Savings Plans — alone worth $2,400–$3,300/month; (2) eliminating the EC2 Reserved Instance contract that is 28% underutilized — a structural commitment misalignment worth $800–$1,200; and (3) right-sizing ElastiCache Redis running at 40% — worth $500–$900/month with no SLA risk.
    <br><br>
    The 15% target is achievable within 6–8 weeks through three low-effort actions alone: EC2 Savings Plans, CloudWatch log retention cleanup, and NAT Gateway VPC Endpoints. The remaining opportunities extend savings to 22–34% over a 90-day horizon.
    <br><br>
    <strong style="color:var(--color-text-primary)">No recommendation here requires architectural redesign or degrades SLA.</strong> All changes are reversible. Risk is concentrated in two areas: EKS node group resizing (requires workload validation) and RDS tier changes (requires staging window).
  </div>
</div>

<hr class="div">

<div class="sec">
  <div class="lbl">Optimization opportunities — sorted by impact · click to expand</div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p1">P1 · Critical</span>
      <span class="opp-title">EC2 on-demand → Savings Plans / Reserved Instances</span>
      <span class="opp-save">$2,400–$3,300/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">EC2 on-demand instances cost $8,200/month at only 45% average utilization. This is the largest single optimization. The workload pattern — variable but predictable — suits a Compute Savings Plan (1-year, no-upfront) over strict Reserved Instances, as Savings Plans apply automatically across instance families and sizes.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$8,200/mo (on-demand)</div>
        <div class="dc"><strong>Savings range</strong>$2,400–$3,300/mo (29–40%)</div>
        <div class="dc"><strong>Bill share</strong>19.6% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-low">Low</span></div>
        <div class="dc"><strong>Operational risk</strong>None — no workload change</div>
        <div class="dc"><strong>Implementation time</strong>1–3 days</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Analyze last 30 days of usage in Cost Explorer → choose commitment level covering ~70% of baseline (never 100% — preserve flex for variable peaks) → purchase Compute Savings Plan. Do NOT purchase before validating utilization baseline.</div>
      </div>
      <div class="hl"><i class="ti ti-info-circle" style="font-size:14px;vertical-align:-2px;margin-right:5px" aria-hidden="true"></i>Pair with the EC2 Reserved Instance audit below — buying new Savings Plans while existing Reserved commitments sit underutilized doubles the waste.</div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p1">P1 · Critical</span>
      <span class="opp-title">EC2 Reserved Instance — utilization gap (72%, 1-year contract)</span>
      <span class="opp-save">$800–$1,200/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">The existing 1-year EC2 Reserved contract ($4,200/mo) runs at 72% utilization, meaning 28% of the commitment is wasted every month. On a 1-year contract, this is ~$14,000 in committed but unrecovered spend annually. The commitment cannot be cancelled, but unused capacity can be offered on the Reserved Instance Marketplace or workloads reshaped to absorb it.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$4,200/mo (RI contract)</div>
        <div class="dc"><strong>Recoverable waste</strong>~$1,176/mo (28% unused)</div>
        <div class="dc"><strong>Bill share</strong>10.0% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-med">Medium</span></div>
        <div class="dc"><strong>Operational risk</strong>Low — no infra change required</div>
        <div class="dc"><strong>Implementation time</strong>1–4 weeks</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Identify which workloads map to this RI → either migrate additional workloads onto these instance types to fill the gap, or list unused capacity on the RI Marketplace. For next renewal: switch to Compute Savings Plans, which have no instance-type lock-in.</div>
      </div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p1">P1 · Critical</span>
      <span class="opp-title">EKS node group right-sizing (3 clusters at 58% util.)</span>
      <span class="opp-save">$1,200–$2,000/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">Three EKS clusters at $6,700/month with 58% average node utilization suggests node groups are overprovisioned by 1–2 instance sizes. With proper autoscaler configuration and right-sized node instance types, 15–30% of cluster cost is recoverable without touching workloads.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$6,700/mo (3 clusters)</div>
        <div class="dc"><strong>Savings range</strong>$1,200–$2,000/mo (18–30%)</div>
        <div class="dc"><strong>Bill share</strong>16.0% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-hi">High</span></div>
        <div class="dc"><strong>Operational risk</strong>Medium — validate per cluster</div>
        <div class="dc"><strong>Implementation time</strong>3–6 weeks</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Deploy VPA in recommendation mode for 2 weeks → collect actual node CPU/memory P95 data → right-size node instance types per cluster → validate in staging with load test → consider Karpenter for smarter bin-packing. Never resize all 3 clusters simultaneously.</div>
      </div>
      <div class="hl"><i class="ti ti-alert-triangle" style="font-size:14px;vertical-align:-2px;margin-right:5px" aria-hidden="true"></i>Highest execution risk in this list. Do this after EC2 Savings Plans and CloudWatch quick wins are captured.</div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p2">P2 · High</span>
      <span class="opp-title">RDS PostgreSQL — right-sizing (multi-AZ, 62% util.)</span>
      <span class="opp-save">$1,500–$2,500/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">RDS at $8,200/month with 62% CPU utilization is a strong right-sizing candidate — the instance is likely 1–2 classes too large. In multi-AZ, the savings from downsizing apply to both primary and standby, doubling the financial impact. After right-sizing, purchasing a 1-year RDS Reserved Instance adds 30–40% on top of the size savings.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$8,200/mo (multi-AZ)</div>
        <div class="dc"><strong>Savings range</strong>$1,500–$2,500/mo (18–30%)</div>
        <div class="dc"><strong>Bill share</strong>19.6% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-med">Medium</span></div>
        <div class="dc"><strong>Operational risk</strong>Medium — requires maintenance window</div>
        <div class="dc"><strong>Implementation time</strong>2–4 weeks</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Export 30-day CloudWatch metrics: CPU P95, FreeableMemory, ReadIOPS, WriteIOPS → use AWS Compute Optimizer recommendation → validate target class in staging with production-representative load → schedule maintenance window (typically &lt;5min failover for multi-AZ). Buy RI only after 30 days on new instance class.</div>
      </div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p2">P2 · High</span>
      <span class="opp-title">ElastiCache Redis right-sizing (40% utilization)</span>
      <span class="opp-save">$500–$900/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">ElastiCache at $2,100/month and only 40% utilization is overprovisioned. A single node type reduction (e.g., cache.r7g.large → cache.r7g.medium, or reducing node count in the cluster) typically saves 25–45% with no impact on cache hit ratio or SLA — provided memory headroom is validated first.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$2,100/mo</div>
        <div class="dc"><strong>Savings range</strong>$500–$900/mo (24–43%)</div>
        <div class="dc"><strong>Bill share</strong>5.0% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-low">Low</span></div>
        <div class="dc"><strong>Operational risk</strong>Low — validate memory usage first</div>
        <div class="dc"><strong>Implementation time</strong>1–2 weeks</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Check CloudWatch: DatabaseMemoryUsagePercentage and CurrConnections over 30 days → if peak memory &lt;60%, downsize node type or reduce replica count → test in non-prod first. Also check cache hit ratio — if &lt;80%, fix caching strategy before resizing.</div>
      </div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p2">P2 · High</span>
      <span class="opp-title">CloudWatch Logs — retention policy + log volume reduction</span>
      <span class="opp-save">$700–$1,200/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">CloudWatch Logs at $2,800/month with a blanket 90-day retention suggests all log groups are retained equally — including high-volume debug and trace logs that have no operational value after 7–14 days. Tiered retention by log class is the fastest, zero-risk cost reduction in this entire report.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$2,800/mo</div>
        <div class="dc"><strong>Savings range</strong>$700–$1,200/mo (25–43%)</div>
        <div class="dc"><strong>Bill share</strong>6.7% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-low">Low</span></div>
        <div class="dc"><strong>Operational risk</strong>None if compliance-reviewed</div>
        <div class="dc"><strong>Implementation time</strong>1–3 days</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Audit all log groups and classify: debug/trace → 7 days; application → 30 days; audit/security → 90 days (export to S3 Glacier for longer). Confirm retention minimums with legal/compliance before changing audit logs. Apply via Terraform or AWS CLI in one pass.</div>
      </div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p2">P2 · High</span>
      <span class="opp-title">NAT Gateway — VPC Endpoints for AWS services</span>
      <span class="opp-save">$400–$700/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">NAT Gateway at $1,200/month across 3 gateways is likely processing significant traffic from EKS pods calling AWS services (S3, ECR, Secrets Manager, SSM) through NAT instead of VPC Endpoints. Gateway Endpoints for S3 and DynamoDB are free; Interface Endpoints for other services cost ~$0.01/hr but eliminate NAT data processing charges at $0.045/GB.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$1,200/mo</div>
        <div class="dc"><strong>Savings range</strong>$400–$700/mo (33–58%)</div>
        <div class="dc"><strong>Bill share</strong>2.9% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-low">Low</span></div>
        <div class="dc"><strong>Operational risk</strong>None — additive VPC change</div>
        <div class="dc"><strong>Implementation time</strong>2–5 days</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Enable VPC Flow Logs → query top destination IPs/services through NAT → create VPC Gateway Endpoints (S3, DynamoDB — free) and Interface Endpoints for ECR, Secrets Manager, SSM. No application code changes required.</div>
      </div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p3">P3 · Medium</span>
      <span class="opp-title">Data Transfer Out — cross-region traffic review</span>
      <span class="opp-save">$400–$800/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">$1,900/month on inter-region data transfer is a signal that services are communicating across regions unnecessarily, or that assets (S3, images) are not edge-cached via CloudFront. Cross-region transfer costs $0.02/GB vs $0 within the same region. A CloudFront distribution in front of S3 and static assets typically reduces outbound data transfer costs by 40–70% while improving latency.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$1,900/mo</div>
        <div class="dc"><strong>Savings range</strong>$400–$800/mo (21–42%)</div>
        <div class="dc"><strong>Bill share</strong>4.5% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-med">Medium</span></div>
        <div class="dc"><strong>Operational risk</strong>Low — CloudFront is additive</div>
        <div class="dc"><strong>Implementation time</strong>1–3 weeks</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Use Cost Explorer → Data Transfer breakdown by source/destination → identify top cross-region flows → consolidate services to single region where possible, or add CloudFront caching. Check if AWS PrivateLink can replace any cross-region API calls.</div>
      </div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p3">P3 · Medium</span>
      <span class="opp-title">Lambda — architecture review (30% util., 12M invocations)</span>
      <span class="opp-save">$200–$400/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">Lambda at $900/month and 30% utilization with 12M monthly invocations suggests functions are over-provisioned in memory or duration. Lambda is billed per GB-second — a function using 512MB can often run on 256MB with the same duration, halving its compute cost. AWS Lambda Power Tuning is a serverless tool that identifies the optimal memory setting automatically.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$900/mo</div>
        <div class="dc"><strong>Savings range</strong>$200–$400/mo (22–44%)</div>
        <div class="dc"><strong>Bill share</strong>2.2% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-low">Low</span></div>
        <div class="dc"><strong>Operational risk</strong>Low — test per function</div>
        <div class="dc"><strong>Implementation time</strong>1–2 weeks</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Deploy AWS Lambda Power Tuning (open source, runs via Step Functions) → get optimal memory recommendation per function → apply and monitor p99 duration → also check for functions with consistently short durations that could be batched to reduce invocation count.</div>
      </div>
    </div>
  </div>

  <div class="opp">
    <div class="opp-h" onclick="tog(this)">
      <span class="badge p4">P4 · Low</span>
      <span class="opp-title">S3 — lifecycle policies and storage class tiering</span>
      <span class="opp-save">$300–$600/mo</span>
      <span class="chev">▾</span>
    </div>
    <div class="opp-b">
      <div class="txt">S3 at $3,100/month across 5 buckets with all objects in S3 Standard is a common waste pattern. Objects older than 30 days rarely require immediate access. S3 Intelligent-Tiering moves objects automatically between frequent and infrequent access tiers at no retrieval cost — suitable for unpredictable access patterns. S3 Glacier Instant Retrieval is ideal for compliance archives.</div>
      <div class="dg">
        <div class="dc"><strong>Current cost</strong>$3,100/mo</div>
        <div class="dc"><strong>Savings range</strong>$300–$600/mo (10–19%)</div>
        <div class="dc"><strong>Bill share</strong>7.4% of total</div>
        <div class="dc"><strong>Effort</strong><span class="badge eff-low">Low</span></div>
        <div class="dc"><strong>Operational risk</strong>None — retrieval latency only for archives</div>
        <div class="dc"><strong>Implementation time</strong>1 week</div>
      </div>
      <div class="dg" style="grid-template-columns:1fr">
        <div class="dc"><strong>Prerequisites</strong>Enable S3 Storage Lens → identify object age distribution per bucket → add lifecycle rules: Standard → Intelligent-Tiering at 30 days; Intelligent-Tiering → Glacier Instant at 90 days for known-cold data. Confirm retrieval latency requirements with application owners before archiving.</div>
      </div>
    </div>
  </div>

</div>

<hr class="div">

<div class="sec">
  <div class="lbl">Savings potential by initiative</div>
  <div class="srow"><span class="slbl">EC2 on-demand → SP/RI</span><div class="sbg"><div class="sbar" style="width:100%;background:#185FA5"></div></div><span class="sval">$2.4–3.3K</span></div>
  <div class="srow"><span class="slbl">RDS right-size + RI</span><div class="sbg"><div class="sbar" style="width:88%;background:#185FA5"></div></div><span class="sval">$1.5–2.5K</span></div>
  <div class="srow"><span class="slbl">EKS node right-sizing</span><div class="sbg"><div class="sbar" style="width:75%;background:#185FA5"></div></div><span class="sval">$1.2–2.0K</span></div>
  <div class="srow"><span class="slbl">CloudWatch cleanup</span><div class="sbg"><div class="sbar" style="width:52%;background:#854F0B"></div></div><span class="sval">$0.7–1.2K</span></div>
  <div class="srow"><span class="slbl">EC2 RI utilization gap</span><div class="sbg"><div class="sbar" style="width:45%;background:#854F0B"></div></div><span class="sval">$0.8–1.2K</span></div>
  <div class="srow"><span class="slbl">ElastiCache resize</span><div class="sbg"><div class="sbar" style="width:38%;background:#854F0B"></div></div><span class="sval">$0.5–0.9K</span></div>
  <div class="srow"><span class="slbl">Data Transfer + CDN</span><div class="sbg"><div class="sbar" style="width:32%;background:#888780"></div></div><span class="sval">$0.4–0.8K</span></div>
  <div class="srow"><span class="slbl">NAT → VPC Endpoints</span><div class="sbg"><div class="sbar" style="width:28%;background:#888780"></div></div><span class="sval">$0.4–0.7K</span></div>
  <div class="srow"><span class="slbl">S3 lifecycle policies</span><div class="sbg"><div class="sbar" style="width:22%;background:#888780"></div></div><span class="sval">$0.3–0.6K</span></div>
  <div class="srow"><span class="slbl">Lambda power tuning</span><div class="sbg"><div class="sbar" style="width:16%;background:#888780"></div></div><span class="sval">$0.2–0.4K</span></div>
</div>

<hr class="div">

<div class="sec">
  <div class="lbl">Risk matrix</div>
  <div class="rgrid">
    <div class="rc"><div class="rl h">High risk</div><div class="rt">EKS node group resizing</div><div class="rd">Requires per-workload load testing. Incorrect sizing causes OOMKilled pods or latency degradation under real traffic.</div></div>
    <div class="rc"><div class="rl m">Medium risk</div><div class="rt">RDS instance class change</div><div class="rd">Burst CPU patterns can be masked by averages. Validate P95/P99 metrics and run staging load test before production change.</div></div>
    <div class="rc"><div class="rl m">Medium risk</div><div class="rt">EC2 RI commitment reshaping</div><div class="rd">RI contracts cannot be cancelled. Changes require workload migration or Marketplace listing — both take time and coordination.</div></div>
    <div class="rc"><div class="rl l">Low risk</div><div class="rt">CloudWatch retention</div><div class="rd">Compliance sign-off required for audit log classes. Application logs are safe to reduce immediately.</div></div>
    <div class="rc"><div class="rl l">Low risk</div><div class="rt">ElastiCache resize</div><div class="rd">Validate peak memory before downsizing. Cache eviction under memory pressure degrades application performance silently.</div></div>
    <div class="rc"><div class="rl l">Low risk</div><div class="rt">NAT → VPC Endpoints</div><div class="rd">Purely additive change. No application code or routing changes. Test connectivity after endpoint creation.</div></div>
  </div>
</div>

<hr class="div">

<div class="sec">
  <div class="lbl">90-day action plan</div>
  <div class="tl">
    <div class="tp">
      <div class="tline"><div class="tdot now"></div><div class="tv"></div></div>
      <div class="tc">
        <div class="tpl now">Weeks 1–2 · Quick wins — zero SLA risk</div>
        <ul class="tl-items">
          <li>Purchase Compute Savings Plans for EC2 on-demand baseline (70% of min usage)</li>
          <li>Set CloudWatch log retention: 7 / 30 / 90 days by log class via Terraform</li>
          <li>Create S3 and DynamoDB Gateway VPC Endpoints (free, 1-hour task)</li>
          <li>Run AWS Lambda Power Tuning on all production functions</li>
          <li>Enable Cost Explorer anomaly detection + budget alert at $38K/month</li>
          <li>Apply mandatory cost tags: env / team / service / cost-center across all resources</li>
        </ul>
      </div>
    </div>
    <div class="tp">
      <div class="tline"><div class="tdot mid"></div><div class="tv"></div></div>
      <div class="tc">
        <div class="tpl mid">Weeks 3–6 · Structural — staged rollout</div>
        <ul class="tl-items">
          <li>Deploy VPA in recommendation mode on all 3 EKS clusters</li>
          <li>Right-size ElastiCache Redis after memory validation</li>
          <li>Add Interface VPC Endpoints: ECR, Secrets Manager, SSM</li>
          <li>Add S3 lifecycle rules: Intelligent-Tiering at 30d, Glacier at 90d</li>
          <li>Begin RDS right-sizing in staging with production load profile</li>
          <li>Analyze EC2 Reserved Instance utilization → plan gap remediation</li>
        </ul>
      </div>
    </div>
    <div class="tp">
      <div class="tline"><div class="tdot lat"></div></div>
      <div class="tc" style="padding-bottom:0">
        <div class="tpl lat">Weeks 7–12 · Governance and long-term commitments</div>
        <ul class="tl-items">
          <li>Apply RDS right-sizing to production after 30-day staging validation</li>
          <li>Apply EKS node group changes per-cluster after VPA data collected</li>
          <li>Purchase 1-year RDS Reserved Instance post right-sizing stabilization</li>
          <li>Add CloudFront in front of S3 to reduce cross-region data transfer</li>
          <li>Establish monthly FinOps review: cost vs. budget, waste delta, tagging compliance</li>
          <li>Evaluate Graviton (ARM) migration for RDS and EKS nodes — additional 10–20%</li>
        </ul>
      </div>
    </div>
  </div>
</div>

<hr class="div">

<div class="sec">
  <div class="lbl">Technical conclusion</div>
  <div class="concl">
    The 15% cost reduction target for Q3 — worth $6,270/month — is <strong>achievable within the first two weeks</strong> through EC2 Savings Plans and CloudWatch retention cleanup alone, without touching a single production workload. The full 90-day program delivers $9,200–$14,100/month in savings (22–34%), well above the business target.
    <br><br>
    <strong>Sequencing is critical.</strong> Purchase Savings Plans and Reserved Instances last, not first — only after right-sizing is complete. Committing to current on-demand levels locks in waste. The correct order: observe → right-size → commit.
    <br><br>
    <strong>The highest-risk items (EKS, RDS) are also the highest-savings items.</strong> Execute them with proper staging validation and they carry acceptable risk. Skip the validation and they carry production risk. The SRE team should own execution with a written rollback procedure per change.
    <br><br>
    With mandatory cost tagging and a monthly FinOps review in place, Hill Valley Tech will prevent this waste from accumulating again — shifting from reactive cost discovery to proactive cost governance.
  </div>
  <div style="margin-top:.75rem;display:flex;gap:8px;flex-wrap:wrap">
    <button onclick="sendPrompt('Generate a Terraform module to set CloudWatch log retention policies for Hill Valley Tech')">Generate CloudWatch Terraform ↗</button>
    <button onclick="sendPrompt('Write an AWS CLI script to identify unused EC2 Reserved Instance capacity for Hill Valley Tech')">EC2 RI audit script ↗</button>
    <button onclick="sendPrompt('Create a FinOps tagging strategy and AWS Config rules for Hill Valley Tech cost allocation')">FinOps tagging strategy ↗</button>
  </div>
</div>

</div>

<script>
function tog(h){
  const b=h.nextElementSibling;
  const c=h.querySelector('.chev');
  const open=b.classList.contains('vis');
  b.classList.toggle('vis',!open);
  c.classList.toggle('open',!open);
}
</script>

