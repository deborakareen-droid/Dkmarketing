import React from "react";

const sections = [
  { id: "about", label: "Sobre" },
  { id: "services", label: "Serviços" },
  { id: "contact", label: "Contato" },
];

function DotNav({ current }) {
  return (
    <nav className="fixed right-6 top-1/2 transform -translate-y-1/2 z-40 hidden md:flex flex-col gap-3">
      {sections.map((s) => (
        <a
          key={s.id}
          href={`#${s.id}`}
          className={`w-3 h-3 rounded-full block transition-all duration-200 ${
            current === s.id ? "scale-125 bg-orange-400" : "bg-neutral-700"
          }`}
          aria-label={`Navegar para ${s.label}`}
        />
      ))}
    </nav>
  );
}

export default function Portfolio() {
  const [current, setCurrent] = React.useState(sections[0].id);

  React.useEffect(() => {
    const observer = new window.IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) setCurrent(entry.target.id);
        });
      },
      { threshold: 0.55 }
    );
    sections.forEach((s) => {
      const el = document.getElementById(s.id);
      if (el) observer.observe(el);
    });
    return () => observer.disconnect();
  }, []);

  return (
    <div
      className="min-h-screen bg-[#0b0b0b] text-[#f7f7f7] font-sans leading-relaxed"
      style={{ fontFamily: "Montserrat, system-ui, sans-serif" }}
    >
      {/* Header */}
      <header className="w-full flex items-center justify-between px-6 py-4 max-w-6xl mx-auto">
        <div className="flex items-center gap-3">
          <div className="w-10 h-10 rounded-lg bg-gradient-to-br from-[#ffa700] to-[#ff7a00] grid place-items-center text-black font-extrabold">
            DK
          </div>
          <span className="font-extrabold tracking-wide">DK Marketing</span>
        </div>
        <div className="hidden md:flex items-center gap-6">
          <a href="#about" className="text-sm opacity-90">
            Sobre
          </a>
          <a href="#services" className="text-sm opacity-90">
            Serviços
          </a>
          <a href="#contact" className="text-sm opacity-90">
            Contato
          </a>
          <a
            href="tel:+5575981383406"
            className="ml-2 inline-flex items-center gap-2 px-4 py-2 rounded-full bg-gradient-to-br from-[#ffa700] to-[#ff7a00] text-black font-bold"
          >
            Entrar em Contato
          </a>
          <a
            href="https://wa.me/5575981383406"
            target="_blank"
            rel="noopener noreferrer"
            className="ml-2 inline-flex items-center gap-2 px-4 py-2 rounded-full bg-green-500 text-white font-bold"
          >
            WhatsApp
          </a>
        </div>
      </header>

      <DotNav current={current} />

      <main className="max-w-6xl mx-auto px-6">
        {/* About Section */}
        <section id="about" className="py-12">
          <h2 className="text-3xl font-bold">Sobre</h2>
          <p className="mt-4 text-neutral-300">
            Agência de Marketing Digital focada em resultados reais!
          </p>
        </section>

        {/* Services Section */}
        <section id="services" className="py-12 border-t border-white/6">
          <h2 className="text-3xl font-bold">Serviços</h2>
          <ul className="mt-4 text-neutral-300 list-disc list-inside">
            <li>Gestão de Redes Sociais</li>
            <li>Criação de Sites</li>
            <li>Design Gráfico</li>
            <li>Gestão de Tráfego Pago</li>
          </ul>
        </section>

        {/* Contact Section */}
        <section id="contact" className="py-12 border-t border-white/6">
          <div className="grid md:grid-cols-2 gap-8">
            <div>
              <h2 className="text-3xl font-bold">Contato</h2>
              <p className="mt-4 text-neutral-300">
                Pronto para dar o próximo passo na sua marca? Fale com a gente e transforme suas ideias em resultados!
              </p>
              <div className="mt-6 space-y-3 text-neutral-200">
                <div>
                  <div className="font-semibold">Email</div>
                  <div className="text-sm">deborakareen@gmail.com</div>
                </div>
                <div>
                  <div className="font-semibold">Social Media</div>
                  <div className="text-sm">
                    @deborakareen • @deborakarenmarketing
                  </div>
                </div>
                <div>
                  <div className="font-semibold">Phone Number</div>
                  <div className="text-sm">(75) 98138-3406</div>
                  <div className="mt-3 flex gap-3 flex-wrap">
                    <a
                      href="tel:+5575981383406"
                      className="inline-block px-4 py-2 rounded-full bg-gradient-to-br from-[#ffa700] to-[#ff7a00] text-black font-bold"
                    >
                      Ligar Agora
                    </a>
                    <a
                      href="https://wa.me/5575981383406"
                      target="_blank"
                      rel="noopener noreferrer"
                      className="inline-block px-4 py-2 rounded-full bg-green-500 text-white font-bold"
                    >
                      WhatsApp
                    </a>
                  </div>
                </div>
              </div>
            </div>
            <div>
              <div className="bg-neutral-900 rounded-lg p-6">
                <h3 className="font-semibold">Mensagem rápida</h3>
                <form
                  className="mt-3 grid gap-3"
                  onSubmit={(e) => {
                    e.preventDefault();
                    alert("Mensagem enviada! (simulação)");
                  }}
                >
                  <input
                    className="w-full bg-neutral-800 px-3 py-2 rounded"
                    placeholder="Seu nome"
                    required
                  />
                  <input
                    className="w-full bg-neutral-800 px-3 py-2 rounded"
                    placeholder="Seu e-mail"
                    required
                  />
                  <textarea
                    className="w-full bg-neutral-800 px-3 py-2 rounded"
                    rows={4}
                    placeholder="Sua mensagem"
                    required
                  />
                  <button
                    type="submit"
                    className="inline-block px-4 py-2 rounded bg-gradient-to-br from-[#ffa700] to-[#ff7a00] text-black font-bold"
                  >
                    Enviar
                  </button>
                </form>
              </div>
            </div>
          </div>
        </section>

        <footer className="py-12 text-center text-neutral-400 border-t border-white/6 mt-12">
          <div>
            Será um prazer trabalhar com a sua empresa e trazer ideias inovadoras que vão te conduzir a um novo patamar.
          </div>
          <div className="mt-6">
            © {new Date().getFullYear()} DK Marketing — Todos os direitos reservados.
          </div>
        </footer>
      </main>
    </div>
  );
}
