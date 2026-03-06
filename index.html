import { useState, useEffect } from "react";

// ─── MOCK DATA ────────────────────────────────────────────────────────────────
const STAFF = ["Nate", "Jenni", "Allice", "Hazel", "Marcus", "Sofia", "Ray", "Dana"];

const INITIAL_KITS = [
  {
    id: "kit-a",
    name: "Outreach Kit A",
    status: "available", // available | checked-out | needs-attention
    checkedOutTo: null,
    checkedOutSince: null,
    event: null,
    returnDate: null,
    condition: "good",
    lastVerified: "2026-02-28",
    items: ["Banner (1)", "Tablecloth (2)", "Clipboards (3)", "Pens (10)", "Brochures (50)", "Name Tags (20)"],
  },
  {
    id: "kit-b",
    name: "Outreach Kit B",
    status: "available",
    checkedOutTo: null,
    checkedOutSince: null,
    event: null,
    returnDate: null,
    condition: "good",
    lastVerified: "2026-03-01",
    items: ["Pop-up Canopy (1)", "Tablecloth (1)", "Clipboards (2)", "Pens (8)", "Brochures (30)", "Laptop Stand (1)"],
  },
];

const INITIAL_REQUESTS = [
  {
    id: "req-1",
    name: "Sofia",
    program: "Health Outreach",
    event: "South Park Health Fair",
    dateNeeded: "2026-03-15",
    dateReturn: "2026-03-15",
    notes: "Bilingual materials preferred",
    status: "pending",
    assignedKit: null,
    submittedAt: "2026-03-05T14:22:00",
  },
];

const INITIAL_TRANSACTIONS = [
  { id: "t1", type: "checkout", kit: "Outreach Kit A", person: "Ray", event: "Capitol Hill Tabling", timestamp: "2026-03-01T09:00:00", notes: "" },
  { id: "t2", type: "return", kit: "Outreach Kit A", person: "Ray", event: "Capitol Hill Tabling", timestamp: "2026-03-01T17:30:00", notes: "All good" },
];

// ─── HELPERS ─────────────────────────────────────────────────────────────────
const fmt = (iso) => {
  if (!iso) return "—";
  const d = new Date(iso);
  return d.toLocaleDateString("en-US", { month: "short", day: "numeric", year: "numeric" });
};
const fmtTime = (iso) => {
  if (!iso) return "—";
  const d = new Date(iso);
  return d.toLocaleTimeString("en-US", { hour: "numeric", minute: "2-digit" }) + " · " + d.toLocaleDateString("en-US", { month: "short", day: "numeric" });
};

// ─── STYLES ──────────────────────────────────────────────────────────────────
const G = {
  pink: "#e8197d",
  pinkDark: "#c4156a",
  pinkLight: "#fce8f3",
  pinkFaint: "#fdf3f9",
  ink: "#1a1225",
  inkMid: "#4a3f58",
  inkLight: "#8b7a9a",
  border: "#e8dff0",
  surface: "#faf8fc",
  white: "#ffffff",
  green: "#1ab86c",
  greenFaint: "#e8f9f1",
  amber: "#f5a623",
  amberFaint: "#fef6e8",
  red: "#e83419",
  redFaint: "#fdecea",
};

const css = {
  app: {
    fontFamily: "'DM Sans', system-ui, sans-serif",
    background: G.surface,
    minHeight: "100vh",
    color: G.ink,
  },
  // Nav
  nav: {
    background: G.white,
    borderBottom: `1px solid ${G.border}`,
    padding: "0 24px",
    display: "flex",
    alignItems: "center",
    justifyContent: "space-between",
    height: 60,
    position: "sticky",
    top: 0,
    zIndex: 100,
  },
  navLogo: {
    display: "flex",
    alignItems: "center",
    gap: 10,
    fontWeight: 700,
    fontSize: 17,
    color: G.ink,
    letterSpacing: "-0.3px",
  },
  navPill: {
    width: 10,
    height: 10,
    borderRadius: "50%",
    background: G.pink,
  },
  navTabs: { display: "flex", gap: 4 },
  navTab: (active) => ({
    padding: "6px 14px",
    borderRadius: 8,
    border: "none",
    cursor: "pointer",
    fontSize: 14,
    fontWeight: active ? 600 : 400,
    background: active ? G.pinkLight : "transparent",
    color: active ? G.pink : G.inkMid,
    transition: "all 0.15s",
  }),
  // Layout
  page: { maxWidth: 900, margin: "0 auto", padding: "32px 24px" },
  pageWide: { maxWidth: 1100, margin: "0 auto", padding: "32px 24px" },
  // Cards
  card: {
    background: G.white,
    border: `1px solid ${G.border}`,
    borderRadius: 16,
    padding: 24,
    marginBottom: 16,
  },
  cardTitle: { fontSize: 16, fontWeight: 700, color: G.ink, marginBottom: 4 },
  cardSub: { fontSize: 13, color: G.inkLight, marginBottom: 0 },
  // Kit cards
  kitCard: (status) => ({
    background: G.white,
    border: `2px solid ${status === "available" ? G.green : status === "needs-attention" ? G.amber : G.border}`,
    borderRadius: 20,
    padding: 24,
    flex: 1,
    minWidth: 260,
    position: "relative",
    overflow: "hidden",
  }),
  kitStatus: (status) => ({
    display: "inline-flex",
    alignItems: "center",
    gap: 6,
    padding: "4px 12px",
    borderRadius: 20,
    fontSize: 12,
    fontWeight: 600,
    letterSpacing: "0.3px",
    textTransform: "uppercase",
    background: status === "available" ? G.greenFaint : status === "needs-attention" ? G.amberFaint : "#f0edf5",
    color: status === "available" ? G.green : status === "needs-attention" ? G.amber : G.inkLight,
  }),
  statusDot: (status) => ({
    width: 7,
    height: 7,
    borderRadius: "50%",
    background: status === "available" ? G.green : status === "needs-attention" ? G.amber : G.inkLight,
  }),
  // Buttons
  btnPrimary: {
    background: G.pink,
    color: G.white,
    border: "none",
    borderRadius: 10,
    padding: "12px 24px",
    fontSize: 15,
    fontWeight: 600,
    cursor: "pointer",
    width: "100%",
    transition: "background 0.15s",
    letterSpacing: "-0.2px",
  },
  btnSecondary: {
    background: "transparent",
    color: G.pink,
    border: `1.5px solid ${G.pink}`,
    borderRadius: 10,
    padding: "10px 20px",
    fontSize: 14,
    fontWeight: 600,
    cursor: "pointer",
    transition: "all 0.15s",
  },
  btnSmall: (variant = "pink") => ({
    background: variant === "pink" ? G.pink : variant === "green" ? G.green : variant === "ghost" ? "transparent" : "#f0edf5",
    color: variant === "ghost" ? G.inkMid : G.white,
    border: variant === "ghost" ? `1px solid ${G.border}` : "none",
    borderRadius: 8,
    padding: "6px 14px",
    fontSize: 13,
    fontWeight: 600,
    cursor: "pointer",
    whiteSpace: "nowrap",
  }),
  // Form
  label: { fontSize: 13, fontWeight: 600, color: G.inkMid, display: "block", marginBottom: 6 },
  input: {
    width: "100%",
    border: `1.5px solid ${G.border}`,
    borderRadius: 10,
    padding: "10px 14px",
    fontSize: 15,
    color: G.ink,
    background: G.white,
    outline: "none",
    boxSizing: "border-box",
    fontFamily: "inherit",
    transition: "border-color 0.15s",
  },
  select: {
    width: "100%",
    border: `1.5px solid ${G.border}`,
    borderRadius: 10,
    padding: "10px 14px",
    fontSize: 15,
    color: G.ink,
    background: G.white,
    outline: "none",
    boxSizing: "border-box",
    fontFamily: "inherit",
    appearance: "none",
    cursor: "pointer",
  },
  textarea: {
    width: "100%",
    border: `1.5px solid ${G.border}`,
    borderRadius: 10,
    padding: "10px 14px",
    fontSize: 15,
    color: G.ink,
    background: G.white,
    outline: "none",
    boxSizing: "border-box",
    fontFamily: "inherit",
    resize: "vertical",
    minHeight: 80,
  },
  formGroup: { marginBottom: 18 },
  // Misc
  row: { display: "flex", gap: 16, flexWrap: "wrap" },
  badge: (c) => ({
    display: "inline-block",
    padding: "2px 10px",
    borderRadius: 20,
    fontSize: 12,
    fontWeight: 600,
    background: c === "pending" ? G.amberFaint : c === "approved" ? G.greenFaint : c === "denied" ? G.redFaint : "#f0edf5",
    color: c === "pending" ? G.amber : c === "approved" ? G.green : c === "denied" ? G.red : G.inkMid,
  }),
  divider: { borderTop: `1px solid ${G.border}`, margin: "20px 0" },
  h1: { fontSize: 26, fontWeight: 800, color: G.ink, marginBottom: 4, letterSpacing: "-0.5px" },
  h2: { fontSize: 20, fontWeight: 700, color: G.ink, marginBottom: 16, letterSpacing: "-0.3px" },
  hint: { fontSize: 13, color: G.inkLight, marginTop: 4 },
  success: {
    background: G.greenFaint,
    border: `1.5px solid ${G.green}`,
    borderRadius: 14,
    padding: "24px",
    textAlign: "center",
  },
};

// ─── QR QUICK ACTION (simulated scan landing) ────────────────────────────────
function QRCheckPage({ kits, onAction, onBack }) {
  const [step, setStep] = useState("select-kit"); // select-kit | select-action | select-person | confirm | done
  const [selectedKit, setSelectedKit] = useState(null);
  const [action, setAction] = useState(null);
  const [person, setPerson] = useState("");
  const [event, setEvent] = useState("");
  const [notes, setNotes] = useState("");
  const [issues, setIssues] = useState(false);

  const kit = kits.find((k) => k.id === selectedKit);

  const handleSubmit = () => {
    onAction({ kitId: selectedKit, action, person, event, notes: issues ? notes : "", timestamp: new Date().toISOString() });
    setStep("done");
  };

  if (step === "done") {
    return (
      <div style={css.page}>
        <div style={css.success}>
          <div style={{ fontSize: 48, marginBottom: 12 }}>{action === "checkout" ? "🧳" : "✅"}</div>
          <div style={{ fontSize: 20, fontWeight: 700, color: G.ink, marginBottom: 8 }}>
            {action === "checkout" ? `${kit?.name} is checked out!` : `${kit?.name} returned — thank you!`}
          </div>
          <div style={{ fontSize: 14, color: G.inkMid, marginBottom: 20 }}>
            {action === "checkout" ? `Logged to ${person} · ${event}` : `Return logged for ${person}`}
          </div>
          {action === "return" && (
            <button style={{ ...css.btnSmall("pink"), padding: "10px 24px", fontSize: 14 }} onClick={() => { setStep("post-report"); }}>
              Quick Post-Event Report →
            </button>
          )}
          {action !== "return" && (
            <button style={{ ...css.btnSmall("ghost"), padding: "10px 24px", fontSize: 14 }} onClick={onBack}>
              Done
            </button>
          )}
        </div>
      </div>
    );
  }

  if (step === "post-report") {
    return <PostEventReport prefill={{ person, event, kit: kit?.name }} onSubmit={() => setStep("report-done")} onBack={onBack} />;
  }
  if (step === "report-done") {
    return (
      <div style={css.page}>
        <div style={css.success}>
          <div style={{ fontSize: 40, marginBottom: 12 }}>🎉</div>
          <div style={{ fontSize: 20, fontWeight: 700, marginBottom: 8 }}>All done!</div>
          <div style={{ fontSize: 14, color: G.inkMid, marginBottom: 20 }}>Return and post-event report saved.</div>
          <button style={{ ...css.btnSmall("ghost"), padding: "10px 24px", fontSize: 14 }} onClick={onBack}>Back to home</button>
        </div>
      </div>
    );
  }

  return (
    <div style={css.page}>
      {/* Header */}
      <button onClick={onBack} style={{ ...css.btnSmall("ghost"), marginBottom: 24 }}>← Back</button>
      <div style={{ marginBottom: 28 }}>
        <div style={{ ...css.h1, fontSize: 22 }}>
          {step === "select-kit" && "Which kit?"}
          {step === "select-action" && kit?.name}
          {step === "select-person" && (action === "checkout" ? "Checking out" : "Returning")}
        </div>
        <div style={css.cardSub}>
          {step === "select-kit" && "Tap the kit you're using"}
          {step === "select-action" && `Status: ${kit?.status === "available" ? "Available" : "Checked out to " + kit?.checkedOutTo}`}
          {step === "select-person" && kit?.name}
        </div>
      </div>

      {/* Step: Select Kit */}
      {step === "select-kit" && (
        <div style={css.row}>
          {kits.map((k) => (
            <div
              key={k.id}
              onClick={() => { setSelectedKit(k.id); setStep("select-action"); }}
              style={{
                ...css.kitCard(k.status),
                cursor: "pointer",
                flex: "1 1 200px",
                transition: "transform 0.1s",
              }}
            >
              <div style={{ fontSize: 32, marginBottom: 10 }}>🧳</div>
              <div style={{ fontWeight: 700, fontSize: 17, marginBottom: 8 }}>{k.name}</div>
              <div style={css.kitStatus(k.status)}>
                <span style={css.statusDot(k.status)} />
                {k.status === "available" ? "Available" : k.status === "checked-out" ? `Out · ${k.checkedOutTo}` : "Needs Attention"}
              </div>
            </div>
          ))}
        </div>
      )}

      {/* Step: Select Action */}
      {step === "select-action" && kit && (
        <div style={css.row}>
          {[
            { id: "checkout", icon: "🧳", label: "Check Out", sub: "I'm taking this kit", disabled: kit.status === "checked-out" },
            { id: "return", icon: "↩️", label: "Return", sub: "I'm bringing it back", disabled: kit.status === "available" },
          ].map((opt) => (
            <div
              key={opt.id}
              onClick={() => { if (!opt.disabled) { setAction(opt.id); setStep("select-person"); } }}
              style={{
                ...css.card,
                flex: "1 1 160px",
                textAlign: "center",
                cursor: opt.disabled ? "not-allowed" : "pointer",
                opacity: opt.disabled ? 0.4 : 1,
                border: `2px solid ${G.border}`,
                transition: "border-color 0.15s",
                margin: 0,
              }}
            >
              <div style={{ fontSize: 36, marginBottom: 10 }}>{opt.icon}</div>
              <div style={{ fontWeight: 700, fontSize: 16, marginBottom: 4 }}>{opt.label}</div>
              <div style={{ fontSize: 13, color: G.inkLight }}>{opt.sub}</div>
            </div>
          ))}
        </div>
      )}

      {/* Step: Person + details */}
      {step === "select-person" && (
        <div style={css.card}>
          <div style={css.formGroup}>
            <label style={css.label}>Your name</label>
            <input
              style={css.input}
              placeholder="Type your name"
              value={person}
              onChange={(e) => setPerson(e.target.value)}
              autoFocus
            />
          </div>

          {action === "checkout" && (
            <div style={css.formGroup}>
              <label style={css.label}>Event or program</label>
              <input style={css.input} placeholder="e.g. South Park Health Fair" value={event} onChange={(e) => setEvent(e.target.value)} />
            </div>
          )}

          {action === "return" && (
            <div style={css.formGroup}>
              <label style={css.label}>Any issues?</label>
              <div style={{ display: "flex", gap: 8 }}>
                {["No issues", "Something to flag"].map((opt) => (
                  <button
                    key={opt}
                    onClick={() => setIssues(opt !== "No issues")}
                    style={{
                      flex: 1,
                      padding: "10px",
                      borderRadius: 8,
                      border: `1.5px solid ${(opt !== "No issues") === issues ? G.pink : G.border}`,
                      background: (opt !== "No issues") === issues ? G.pinkLight : G.white,
                      color: (opt !== "No issues") === issues ? G.pink : G.ink,
                      fontSize: 14,
                      fontWeight: 600,
                      cursor: "pointer",
                      fontFamily: "inherit",
                    }}
                  >
                    {opt}
                  </button>
                ))}
              </div>
              {issues && (
                <textarea
                  style={{ ...css.textarea, marginTop: 10 }}
                  placeholder="What's missing or damaged?"
                  value={notes}
                  onChange={(e) => setNotes(e.target.value)}
                />
              )}
            </div>
          )}

          <button
            style={{ ...css.btnPrimary, opacity: !person || (action === "checkout" && !event) ? 0.5 : 1 }}
            disabled={!person || (action === "checkout" && !event)}
            onClick={handleSubmit}
          >
            {action === "checkout" ? "Confirm Check-Out →" : "Confirm Return →"}
          </button>
        </div>
      )}
    </div>
  );
}

// ─── REQUEST FORM ─────────────────────────────────────────────────────────────
function RequestForm({ onSubmit, onBack }) {
  const [form, setForm] = useState({ name: "", email: "", program: "", event: "", dateNeeded: "", dateReturn: "", notes: "" });
  const [done, setDone] = useState(false);

  const set = (k) => (e) => setForm((f) => ({ ...f, [k]: e.target.value }));
  const valid = form.name && form.program && form.event && form.dateNeeded;

  const handleSubmit = () => {
    onSubmit({ ...form, id: "req-" + Date.now(), status: "pending", submittedAt: new Date().toISOString(), assignedKit: null });
    setDone(true);
  };

  if (done) {
    return (
      <div style={css.page}>
        <div style={css.success}>
          <div style={{ fontSize: 40, marginBottom: 12 }}>📬</div>
          <div style={{ fontSize: 20, fontWeight: 700, marginBottom: 8 }}>Request submitted!</div>
          <div style={{ fontSize: 14, color: G.inkMid, marginBottom: 20 }}>
            Someone will confirm your kit assignment by email. You don't need to do anything else right now.
          </div>
          <button style={{ ...css.btnSmall("ghost"), padding: "10px 24px", fontSize: 14 }} onClick={onBack}>Back to home</button>
        </div>
      </div>
    );
  }

  return (
    <div style={css.page}>
      <button onClick={onBack} style={{ ...css.btnSmall("ghost"), marginBottom: 24 }}>← Back</button>
      <div style={{ marginBottom: 28 }}>
        <div style={css.h1}>Request Outreach Materials</div>
        <div style={css.cardSub}>You don't need to pick a specific kit — we'll assign one for you.</div>
      </div>

      <div style={css.card}>
        <div style={css.row}>
          <div style={{ ...css.formGroup, flex: 1 }}>
            <label style={css.label}>Your name</label>
            <input style={css.input} value={form.name} onChange={set("name")} placeholder="Full name" />
          </div>
          <div style={{ ...css.formGroup, flex: 1 }}>
            <label style={css.label}>Email</label>
            <input style={css.input} value={form.email} onChange={set("email")} placeholder="you@acrs.org" type="email" />
          </div>
        </div>

        <div style={css.formGroup}>
          <label style={css.label}>Program / team</label>
          <input style={css.input} value={form.program} onChange={set("program")} placeholder="e.g. Health Outreach, Immigration Services" />
        </div>

        <div style={css.formGroup}>
          <label style={css.label}>Event name</label>
          <input style={css.input} value={form.event} onChange={set("event")} placeholder="e.g. Beacon Hill Community Fair" />
        </div>

        <div style={css.row}>
          <div style={{ ...css.formGroup, flex: 1 }}>
            <label style={css.label}>Date needed</label>
            <input style={css.input} value={form.dateNeeded} onChange={set("dateNeeded")} type="date" />
          </div>
          <div style={{ ...css.formGroup, flex: 1 }}>
            <label style={css.label}>Return date</label>
            <input style={css.input} value={form.dateReturn} onChange={set("dateReturn")} type="date" />
          </div>
        </div>

        <div style={css.formGroup}>
          <label style={css.label}>Anything else we should know? <span style={{ fontWeight: 400, color: G.inkLight }}>(optional)</span></label>
          <textarea style={css.textarea} value={form.notes} onChange={set("notes")} placeholder="Special needs, large crowd expected, bilingual materials needed, etc." />
        </div>

        <button style={{ ...css.btnPrimary, opacity: valid ? 1 : 0.5 }} disabled={!valid} onClick={handleSubmit}>
          Submit Request →
        </button>
      </div>
    </div>
  );
}

// ─── POST-EVENT REPORT ────────────────────────────────────────────────────────
function PostEventReport({ prefill = {}, onSubmit, onBack }) {
  const [form, setForm] = useState({
    person: prefill.person || "",
    event: prefill.event || "",
    kit: prefill.kit || "",
    attendance: "",
    went: "",
    improve: "",
    kitCondition: "good",
  });
  const [done, setDone] = useState(false);
  const set = (k) => (e) => setForm((f) => ({ ...f, [k]: e.target.value }));
  const valid = form.person && form.event && form.attendance && form.went;

  if (done) {
    return (
      <div style={css.page}>
        <div style={css.success}>
          <div style={{ fontSize: 40, marginBottom: 12 }}>🎉</div>
          <div style={{ fontSize: 20, fontWeight: 700, marginBottom: 8 }}>Report submitted!</div>
          <div style={{ fontSize: 14, color: G.inkMid, marginBottom: 20 }}>Thanks for closing the loop — this helps us track outreach impact.</div>
          <button style={{ ...css.btnSmall("ghost"), padding: "10px 24px", fontSize: 14 }} onClick={onBack}>Back to home</button>
        </div>
      </div>
    );
  }

  return (
    <div style={css.page}>
      {!prefill.event && <button onClick={onBack} style={{ ...css.btnSmall("ghost"), marginBottom: 24 }}>← Back</button>}
      <div style={{ marginBottom: 28 }}>
        <div style={css.h1}>Post-Event Report</div>
        <div style={css.cardSub}>Just a few quick questions — takes about 2 minutes.</div>
      </div>

      <div style={css.card}>
        <div style={css.row}>
          <div style={{ ...css.formGroup, flex: 1 }}>
            <label style={css.label}>Your name</label>
            {prefill.person
              ? <div style={{ ...css.input, background: G.surface, color: G.inkMid }}>{prefill.person}</div>
              : <input style={css.input} value={form.person} onChange={set("person")} placeholder="Your name" />}
          </div>
          <div style={{ ...css.formGroup, flex: 1 }}>
            <label style={css.label}>Event</label>
            {prefill.event
              ? <div style={{ ...css.input, background: G.surface, color: G.inkMid }}>{prefill.event}</div>
              : <input style={css.input} value={form.event} onChange={set("event")} placeholder="Event name" />}
          </div>
        </div>

        <div style={css.formGroup}>
          <label style={css.label}>Estimated attendance</label>
          <div style={{ display: "flex", flexWrap: "wrap", gap: 8 }}>
            {["Under 20", "20–50", "50–100", "100–200", "200+"].map((opt) => (
              <button
                key={opt}
                onClick={() => setForm((f) => ({ ...f, attendance: opt }))}
                style={{
                  padding: "8px 16px",
                  borderRadius: 8,
                  border: `1.5px solid ${form.attendance === opt ? G.pink : G.border}`,
                  background: form.attendance === opt ? G.pinkLight : G.white,
                  color: form.attendance === opt ? G.pink : G.ink,
                  fontWeight: form.attendance === opt ? 700 : 400,
                  fontSize: 14,
                  cursor: "pointer",
                  fontFamily: "inherit",
                }}
              >
                {opt}
              </button>
            ))}
          </div>
        </div>

        <div style={css.formGroup}>
          <label style={css.label}>What went well?</label>
          <textarea style={css.textarea} value={form.went} onChange={set("went")} placeholder="Community response, connections made, materials used well..." />
        </div>

        <div style={css.formGroup}>
          <label style={css.label}>Anything to improve next time? <span style={{ fontWeight: 400, color: G.inkLight }}>(optional)</span></label>
          <textarea style={css.textarea} value={form.improve} onChange={set("improve")} placeholder="Logistics, materials, timing..." />
        </div>

        <div style={css.formGroup}>
          <label style={css.label}>Kit condition at return</label>
          <div style={{ display: "flex", gap: 8 }}>
            {[{ v: "good", label: "All good ✅" }, { v: "minor", label: "Minor issue 🔧" }, { v: "missing", label: "Something missing ⚠️" }].map((opt) => (
              <button
                key={opt.v}
                onClick={() => setForm((f) => ({ ...f, kitCondition: opt.v }))}
                style={{
                  flex: 1,
                  padding: "10px",
                  borderRadius: 8,
                  border: `1.5px solid ${form.kitCondition === opt.v ? G.pink : G.border}`,
                  background: form.kitCondition === opt.v ? G.pinkLight : G.white,
                  color: form.kitCondition === opt.v ? G.pink : G.ink,
                  fontSize: 13,
                  fontWeight: 600,
                  cursor: "pointer",
                  fontFamily: "inherit",
                }}
              >
                {opt.label}
              </button>
            ))}
          </div>
        </div>

        <button style={{ ...css.btnPrimary, opacity: valid ? 1 : 0.5 }} disabled={!valid} onClick={() => { onSubmit && onSubmit(form); setDone(true); }}>
          Submit Report →
        </button>
      </div>
    </div>
  );
}

// ─── ADMIN DASHBOARD ──────────────────────────────────────────────────────────
function AdminDashboard({ kits, requests, transactions, onApprove, onDeny, onMarkAttention }) {
  const [tab, setTab] = useState("kits");
  const pending = requests.filter((r) => r.status === "pending");

  return (
    <div style={css.pageWide}>
      {/* Header */}
      <div style={{ display: "flex", alignItems: "center", justifyContent: "space-between", marginBottom: 28, flexWrap: "wrap", gap: 12 }}>
        <div>
          <div style={css.h1}>Kit Dashboard</div>
          <div style={css.cardSub}>Admin view · ACRS Outreach</div>
        </div>
        {pending.length > 0 && (
          <div style={{ background: G.amberFaint, border: `1.5px solid ${G.amber}`, borderRadius: 10, padding: "8px 16px", fontSize: 13, fontWeight: 600, color: G.amber }}>
            {pending.length} pending request{pending.length > 1 ? "s" : ""}
          </div>
        )}
      </div>

      {/* Kit status cards */}
      <div style={{ ...css.row, marginBottom: 24 }}>
        {kits.map((k) => (
          <div key={k.id} style={css.kitCard(k.status)}>
            <div style={{ display: "flex", alignItems: "flex-start", justifyContent: "space-between", marginBottom: 12 }}>
              <div style={{ fontSize: 28 }}>🧳</div>
              <span style={css.kitStatus(k.status)}>
                <span style={css.statusDot(k.status)} />
                {k.status === "available" ? "Available" : k.status === "checked-out" ? "Checked Out" : "Needs Attention"}
              </span>
            </div>
            <div style={{ fontWeight: 700, fontSize: 18, marginBottom: 4 }}>{k.name}</div>
            {k.status === "checked-out" && (
              <div style={{ fontSize: 13, color: G.inkMid, marginBottom: 12 }}>
                <div>👤 {k.checkedOutTo}</div>
                <div>📋 {k.event}</div>
                <div>🕐 Since {fmt(k.checkedOutSince)}</div>
                {k.returnDate && <div>📅 Return by {fmt(k.returnDate)}</div>}
              </div>
            )}
            {k.status === "available" && (
              <div style={{ fontSize: 13, color: G.inkLight, marginBottom: 12 }}>Last verified {fmt(k.lastVerified)}</div>
            )}
            <div style={{ display: "flex", gap: 8, flexWrap: "wrap" }}>
              {k.status !== "needs-attention" && (
                <button style={css.btnSmall("ghost")} onClick={() => onMarkAttention(k.id)}>Flag issue</button>
              )}
              {k.status === "needs-attention" && (
                <button style={css.btnSmall("green")} onClick={() => onMarkAttention(k.id, "clear")}>Mark resolved</button>
              )}
            </div>
          </div>
        ))}
      </div>

      {/* Tabs */}
      <div style={{ display: "flex", gap: 4, marginBottom: 20, borderBottom: `1px solid ${G.border}`, paddingBottom: 4 }}>
        {[
          { id: "kits", label: "Requests" + (pending.length ? ` (${pending.length})` : "") },
          { id: "log", label: "Activity Log" },
        ].map((t) => (
          <button key={t.id} onClick={() => setTab(t.id)} style={css.navTab(tab === t.id)}>{t.label}</button>
        ))}
      </div>

      {/* Requests */}
      {tab === "kits" && (
        <div>
          {requests.length === 0 && <div style={{ color: G.inkLight, fontSize: 14 }}>No requests yet.</div>}
          {requests.map((r) => (
            <div key={r.id} style={css.card}>
              <div style={{ display: "flex", alignItems: "flex-start", justifyContent: "space-between", flexWrap: "wrap", gap: 12 }}>
                <div style={{ flex: 1 }}>
                  <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 6, flexWrap: "wrap" }}>
                    <span style={{ fontWeight: 700, fontSize: 16 }}>{r.name}</span>
                    <span style={css.badge(r.status)}>{r.status}</span>
                    {r.assignedKit && <span style={{ fontSize: 13, color: G.inkLight }}>→ {r.assignedKit}</span>}
                  </div>
                  <div style={{ fontSize: 13, color: G.inkMid, display: "flex", gap: 16, flexWrap: "wrap" }}>
                    <span>📋 {r.event}</span>
                    <span>🏢 {r.program}</span>
                    <span>📅 {fmt(r.dateNeeded)}{r.dateReturn && ` – ${fmt(r.dateReturn)}`}</span>
                    <span style={{ color: G.inkLight }}>Submitted {fmtTime(r.submittedAt)}</span>
                  </div>
                  {r.notes && <div style={{ fontSize: 13, color: G.inkLight, marginTop: 6 }}>💬 {r.notes}</div>}
                </div>
                {r.status === "pending" && (
                  <div style={{ display: "flex", gap: 8, alignItems: "center", flexWrap: "wrap" }}>
                    <select
                      style={{ ...css.select, width: "auto", fontSize: 13, padding: "6px 12px" }}
                      onChange={(e) => e.target.value && onApprove(r.id, e.target.value)}
                      defaultValue=""
                    >
                      <option value="" disabled>Assign kit…</option>
                      {kits.filter((k) => k.status === "available").map((k) => (
                        <option key={k.id} value={k.name}>{k.name}</option>
                      ))}
                    </select>
                    <button style={css.btnSmall("ghost")} onClick={() => onDeny(r.id)}>Deny</button>
                  </div>
                )}
              </div>
            </div>
          ))}
        </div>
      )}

      {/* Activity log */}
      {tab === "log" && (
        <div>
          {transactions.length === 0 && <div style={{ color: G.inkLight, fontSize: 14 }}>No activity yet.</div>}
          {[...transactions].reverse().map((t) => (
            <div key={t.id} style={{ ...css.card, display: "flex", alignItems: "center", gap: 16, padding: "14px 20px" }}>
              <div style={{ fontSize: 22 }}>{t.type === "checkout" ? "🧳" : t.type === "return" ? "↩️" : "📋"}</div>
              <div style={{ flex: 1 }}>
                <div style={{ fontWeight: 600, fontSize: 14 }}>
                  {t.type === "checkout" ? "Checked out" : t.type === "return" ? "Returned" : "Report"} · {t.kit}
                </div>
                <div style={{ fontSize: 13, color: G.inkMid }}>
                  {t.person}{t.event ? ` · ${t.event}` : ""}
                </div>
                {t.notes && <div style={{ fontSize: 12, color: G.inkLight, marginTop: 2 }}>⚠️ {t.notes}</div>}
              </div>
              <div style={{ fontSize: 12, color: G.inkLight, whiteSpace: "nowrap" }}>{fmtTime(t.timestamp)}</div>
            </div>
          ))}
        </div>
      )}
    </div>
  );
}

// ─── HOME ─────────────────────────────────────────────────────────────────────
function Home({ kits, onNavigate }) {
  const available = kits.filter((k) => k.status === "available").length;

  return (
    <div style={css.page}>
      {/* Hero */}
      <div style={{ marginBottom: 36, paddingTop: 8 }}>
        <div style={{ fontSize: 13, fontWeight: 600, color: G.pink, letterSpacing: "1px", textTransform: "uppercase", marginBottom: 10 }}>
          ACRS Outreach
        </div>
        <div style={{ ...css.h1, fontSize: 30 }}>Outreach Kit Portal</div>
        <div style={{ fontSize: 15, color: G.inkMid, marginTop: 6 }}>
          {available === 2 ? "Both kits are available right now." : available === 1 ? "One kit is available." : "Both kits are currently checked out."}
        </div>
      </div>

      {/* Kit status strip */}
      <div style={{ ...css.row, marginBottom: 32 }}>
        {kits.map((k) => (
          <div key={k.id} style={{ ...css.kitCard(k.status), flex: "1 1 180px", padding: "16px 20px" }}>
            <div style={{ display: "flex", align: "center", gap: 10, marginBottom: 6 }}>
              <span style={{ fontSize: 22 }}>🧳</span>
              <span style={{ fontWeight: 700, fontSize: 15 }}>{k.name}</span>
            </div>
            <span style={css.kitStatus(k.status)}>
              <span style={css.statusDot(k.status)} />
              {k.status === "available" ? "Available" : k.status === "checked-out" ? `Out · ${k.checkedOutTo}` : "Needs Attention"}
            </span>
          </div>
        ))}
      </div>

      {/* Actions */}
      <div style={css.h2}>What do you need?</div>
      <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(240px, 1fr))", gap: 16, marginBottom: 12 }}>
        {[
          {
            id: "request",
            icon: "📬",
            title: "Request a Kit",
            sub: "Submit a request for an upcoming event",
            color: G.pink,
          },
          {
            id: "checkinout",
            icon: "🔄",
            title: "Check In / Out",
            sub: "Quick tap to log a pickup or return",
            color: G.green,
          },
          {
            id: "report",
            icon: "📊",
            title: "Post-Event Report",
            sub: "2-minute wrap-up after your event",
            color: "#7b61ff",
          },
        ].map((a) => (
          <div
            key={a.id}
            onClick={() => onNavigate(a.id)}
            style={{
              background: G.white,
              border: `1.5px solid ${G.border}`,
              borderRadius: 16,
              padding: "22px 20px",
              cursor: "pointer",
              transition: "border-color 0.15s, box-shadow 0.15s",
              display: "flex",
              flexDirection: "column",
              gap: 8,
            }}
          >
            <div style={{ fontSize: 30 }}>{a.icon}</div>
            <div style={{ fontWeight: 700, fontSize: 16, color: G.ink }}>{a.title}</div>
            <div style={{ fontSize: 13, color: G.inkLight, lineHeight: 1.4 }}>{a.sub}</div>
            <div style={{ marginTop: 4, fontSize: 13, fontWeight: 600, color: a.color }}>Get started →</div>
          </div>
        ))}
      </div>

      {/* QR hint */}
      <div style={{ background: G.pinkFaint, border: `1px dashed ${G.pink}`, borderRadius: 12, padding: "14px 18px", display: "flex", alignItems: "center", gap: 12 }}>
        <div style={{ fontSize: 24 }}>📱</div>
        <div>
          <div style={{ fontSize: 14, fontWeight: 600, color: G.ink }}>QR codes make check-in/out even faster</div>
          <div style={{ fontSize: 13, color: G.inkMid }}>Scan the code inside the kit lid to jump straight to the check-in/out screen.</div>
        </div>
      </div>
    </div>
  );
}

// ─── PASSCODE MODAL ───────────────────────────────────────────────────────────
function PasscodeModal({ onSuccess, onClose }) {
  const [digits, setDigits] = useState(["", "", "", ""]);
  const [error, setError] = useState(false);
  const ADMIN_PASSCODE = "3639";
  const inputRefs = [
    { current: null }, { current: null }, { current: null }, { current: null }
  ];

  const handleDigit = (i, val) => {
    if (!/^\d?$/.test(val)) return;
    const next = [...digits];
    next[i] = val;
    setDigits(next);
    setError(false);
    if (val && i < 3) {
      document.getElementById("pc-" + (i+1))?.focus();
    }
    if (next.every(Boolean)) {
      const code = next.join("");
      if (code === ADMIN_PASSCODE) {
        setTimeout(onSuccess, 120);
      } else {
        setError(true);
        setDigits(["", "", "", ""]);
        setTimeout(() => document.getElementById("pc-0")?.focus(), 80);
      }
    }
  };

  const handleKey = (i, e) => {
    if (e.key === "Backspace" && !digits[i] && i > 0) {
      document.getElementById("pc-" + (i-1))?.focus();
    }
    if (e.key === "Escape") onClose();
  };

  return (
    <div style={{
      position: "fixed", inset: 0, background: "rgba(26,18,37,0.55)", backdropFilter: "blur(4px)",
      display: "flex", alignItems: "center", justifyContent: "center", zIndex: 999,
    }}>
      <div style={{
        background: G.white, borderRadius: 20, padding: "36px 32px", width: 300,
        boxShadow: "0 24px 60px rgba(0,0,0,0.18)", textAlign: "center",
      }}>
        <div style={{ fontSize: 32, marginBottom: 12 }}>🔒</div>
        <div style={{ fontSize: 18, fontWeight: 700, color: G.ink, marginBottom: 6 }}>Admin Access</div>
        <div style={{ fontSize: 13, color: G.inkLight, marginBottom: 24 }}>Enter your 4-digit passcode</div>

        <div style={{ display: "flex", gap: 12, justifyContent: "center", marginBottom: 20 }}>
          {digits.map((d, i) => (
            <input
              key={i}
              id={"pc-" + i}
              type="password"
              inputMode="numeric"
              maxLength={1}
              value={d}
              autoFocus={i === 0}
              onChange={(e) => handleDigit(i, e.target.value)}
              onKeyDown={(e) => handleKey(i, e)}
              style={{
                width: 52, height: 56, textAlign: "center", fontSize: 22, fontWeight: 700,
                border: "2px solid " + (error ? G.red : d ? G.pink : G.border),
                borderRadius: 12, outline: "none", fontFamily: "inherit", color: G.ink,
                background: error ? G.redFaint : d ? G.pinkFaint : G.white,
                transition: "border-color 0.15s, background 0.15s",
              }}
            />
          ))}
        </div>

        {error && (
          <div style={{ fontSize: 13, color: G.red, fontWeight: 600, marginBottom: 16 }}>
            Incorrect passcode — try again
          </div>
        )}

        <button onClick={onClose} style={{ ...css.btnSmall("ghost"), width: "100%", padding: "10px" }}>
          Cancel
        </button>
      </div>
    </div>
  );
}

// ─── ROOT APP ─────────────────────────────────────────────────────────────────
export default function App() {
  const [view, setView] = useState("home");
  const [kits, setKits] = useState(INITIAL_KITS);
  const [requests, setRequests] = useState(INITIAL_REQUESTS);
  const [transactions, setTransactions] = useState(INITIAL_TRANSACTIONS);
  const [adminUnlocked, setAdminUnlocked] = useState(false);
  const [showPasscode, setShowPasscode] = useState(false);

  const isAdmin = view === "admin";

  // ── handlers ──
  const handleCheckAction = ({ kitId, action, person, event, notes, timestamp }) => {
    setKits((prev) =>
      prev.map((k) =>
        k.id !== kitId
          ? k
          : action === "checkout"
          ? { ...k, status: "checked-out", checkedOutTo: person, checkedOutSince: timestamp, event }
          : { ...k, status: "available", checkedOutTo: null, checkedOutSince: null, event: null }
      )
    );
    setTransactions((prev) => [
      ...prev,
      { id: "t" + Date.now(), type: action, kit: kits.find((k) => k.id === kitId)?.name, person, event, timestamp, notes },
    ]);
  };

  const handleRequest = (req) => {
    setRequests((prev) => [...prev, req]);
  };

  const handleApprove = (reqId, kitName) => {
    setRequests((prev) => prev.map((r) => (r.id === reqId ? { ...r, status: "approved", assignedKit: kitName } : r)));
  };

  const handleDeny = (reqId) => {
    setRequests((prev) => prev.map((r) => (r.id === reqId ? { ...r, status: "denied" } : r)));
  };

  const handleMarkAttention = (kitId, mode) => {
    setKits((prev) =>
      prev.map((k) => (k.id !== kitId ? k : { ...k, status: mode === "clear" ? "available" : "needs-attention" }))
    );
  };

  return (
    <div style={css.app}>
      {/* Google Font */}
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&display=swap');
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background: #faf8fc; }
        button:hover { filter: brightness(0.95); }
        input:focus, select:focus, textarea:focus { border-color: #e8197d !important; }
      `}</style>

      {/* Nav */}
      <nav style={css.nav}>
        <div style={css.navLogo} onClick={() => setView("home")} role="button">
          <div style={css.navPill} />
          KitTrack
        </div>
        <div style={css.navTabs}>
          <button style={css.navTab(view === "home" || ["request","checkinout","report"].includes(view))} onClick={() => setView("home")}>Staff</button>
          <button style={css.navTab(view === "admin")} onClick={() => {
            if (adminUnlocked) { setView("admin"); } else { setShowPasscode(true); }
          }}>
            Admin {requests.filter((r) => r.status === "pending").length > 0 && (
              <span style={{ background: G.pink, color: "white", borderRadius: "50%", width: 16, height: 16, display: "inline-flex", alignItems: "center", justifyContent: "center", fontSize: 10, fontWeight: 700, marginLeft: 6 }}>
                {requests.filter((r) => r.status === "pending").length}
              </span>
            )}
          </button>
        </div>
      </nav>

      {/* Passcode modal */}
      {showPasscode && (
        <PasscodeModal
          onSuccess={() => { setAdminUnlocked(true); setShowPasscode(false); setView("admin"); }}
          onClose={() => setShowPasscode(false)}
        />
      )}

      {/* Views */}
      {view === "home" && <Home kits={kits} onNavigate={setView} />}
      {view === "request" && <RequestForm onSubmit={handleRequest} onBack={() => setView("home")} />}
      {view === "checkinout" && <QRCheckPage kits={kits} onAction={handleCheckAction} onBack={() => setView("home")} />}
      {view === "report" && <PostEventReport onSubmit={() => {}} onBack={() => setView("home")} />}
      {view === "admin" && (
        <AdminDashboard
          kits={kits}
          requests={requests}
          transactions={transactions}
          onApprove={handleApprove}
          onDeny={handleDeny}
          onMarkAttention={handleMarkAttention}
        />
      )}
    </div>
  );
}
