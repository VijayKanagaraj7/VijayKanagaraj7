import { useState, useEffect } from 'react';
import { Badge } from '@/components/ui/badge';
import { Card } from '@/components/ui/card';
import heroCoding from '@/assets/hero-coding.jpg';

const Index = () => {
  const [visibleSection, setVisibleSection] = useState(0);

  useEffect(() => {
    const timer = setInterval(() => {
      setVisibleSection(prev => (prev + 1) % 5);
    }, 3000);
    return () => clearInterval(timer);
  }, []);

  const techStacks = [
    {
      category: "AI & Machine Learning",
      technologies: ["PyTorch", "TensorFlow", "Transformers", "LangChain", "Hugging Face", "OpenAI", "LlamaIndex"],
      description: "Orchestrating symphonies of neural architecture"
    },
    {
      category: "Programming Languages", 
      technologies: ["Python", "JavaScript", "TypeScript", "Java", "C++", "SQL"],
      description: "Polyglottal virtuosity in computational linguistics"
    },
    {
      category: "Cloud & MLOps",
      technologies: ["AWS SageMaker", "Docker", "Kubernetes", "MLflow", "Kubeflow", "Apache Airflow"],
      description: "Architecting scalable intelligence infrastructure"
    },
    {
      category: "Data Science",
      technologies: ["Pandas", "NumPy", "Scikit-learn", "XGBoost", "Tableau", "Power BI"],
      description: "Transmuting raw data into crystalline insights"
    }
  ];

  const specializations = [
    { icon: "🧬", title: "Artificial Intelligence", description: "Architecting cognition from silicon and code" },
    { icon: "🔮", title: "Generative AI", description: "Conjuring creativity through autoregressive alchemy" },
    { icon: "🧠", title: "Machine Learning", description: "Sculpting intelligence from probabilistic paradigms" },
    { icon: "📊", title: "Data Science", description: "Extracting omniscience from chaotic information" },
    { icon: "🔬", title: "Research & Innovation", description: "Pioneering uncharted territories of computation" }
  ];

  return (
    <div className="min-h-screen bg-gradient-to-br from-background via-background to-secondary/20 relative overflow-hidden">
      {/* Animated background particles */}
      <div className="absolute inset-0 overflow-hidden">
        {[...Array(50)].map((_, i) => (
          <div
            key={i}
            className="absolute w-1 h-1 bg-primary/30 rounded-full animate-cosmic-drift"
            style={{
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 20}s`,
              animationDuration: `${15 + Math.random() * 10}s`
            }}
          />
        ))}
      </div>

      {/* Neural network grid background */}
      <div className="absolute inset-0 opacity-10">
        <svg className="w-full h-full" viewBox="0 0 100 100">
          <defs>
            <pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse">
              <path d="M 10 0 L 0 0 0 10" fill="none" stroke="currentColor" strokeWidth="0.5"/>
            </pattern>
          </defs>
          <rect width="100%" height="100%" fill="url(#grid)" />
        </svg>
      </div>

      <div className="container mx-auto px-6 py-8 relative z-10">
        {/* Hero Section */}
        <section className="text-center mb-16 animate-fade-in-up">
          <div className="relative inline-block mb-8">
            <img 
              src={heroCoding} 
              alt="Futuristic coding environment"
              className="w-96 h-64 object-cover rounded-2xl shadow-glow-primary animate-glow-pulse"
            />
            <div className="absolute inset-0 bg-gradient-neural opacity-20 rounded-2xl"></div>
          </div>
          
          <h1 className="text-6xl font-bold bg-gradient-cosmic bg-clip-text text-transparent mb-4 animate-neural-pulse">
            Vijay Kanagaraj
          </h1>
          
          <div className="text-xl text-muted-foreground mb-6 max-w-3xl mx-auto leading-relaxed">
            <span className="text-accent font-semibold">Artificer</span> of artificial intelligence and{' '}
            <span className="text-primary font-semibold">connoisseur</span> of computational intricacies.{' '}
            Navigating the <span className="text-accent font-semibold">arcane</span> realms where mathematics meets philosophy,{' '}
            and logic transcends automation.
          </div>

          <div className="flex flex-wrap justify-center gap-3 mb-8">
            <Badge variant="secondary" className="bg-primary/20 text-primary border-primary/30 hover:bg-primary/30 transition-all duration-300">
              🧬 AI Architect
            </Badge>
            <Badge variant="secondary" className="bg-accent/20 text-accent border-accent/30 hover:bg-accent/30 transition-all duration-300">
              🔮 GenAI Specialist
            </Badge>
            <Badge variant="secondary" className="bg-primary/20 text-primary border-primary/30 hover:bg-primary/30 transition-all duration-300">
              📊 Data Alchemist
            </Badge>
          </div>
        </section>

        {/* Specializations Grid */}
        <section className="mb-16">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-neural bg-clip-text text-transparent">
            Domains of Expertise
          </h2>
          
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            {specializations.map((spec, index) => (
              <Card key={index} className="p-6 bg-card/50 border-border/50 hover:border-primary/50 transition-all duration-500 hover:shadow-glow-primary animate-float group">
                <div className="text-4xl mb-4 group-hover:animate-glow-pulse">{spec.icon}</div>
                <h3 className="text-xl font-semibold mb-3 text-foreground">{spec.title}</h3>
                <p className="text-muted-foreground leading-relaxed">{spec.description}</p>
              </Card>
            ))}
          </div>
        </section>

        {/* Tech Stack Showcase */}
        <section className="mb-16">
          <h2 className="text-4xl font-bold text-center mb-12 bg-gradient-cosmic bg-clip-text text-transparent">
            Technological Arsenal
          </h2>
          
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
            {techStacks.map((stack, index) => (
              <Card 
                key={index} 
                className={`p-8 bg-card/30 border-border/30 transition-all duration-700 hover:border-accent/50 hover:shadow-glow-accent ${
                  visibleSection === index ? 'animate-neural-pulse' : ''
                }`}
              >
                <h3 className="text-2xl font-bold mb-4 text-accent">{stack.category}</h3>
                <p className="text-muted-foreground mb-6 italic">{stack.description}</p>
                
                <div className="flex flex-wrap gap-2">
                  {stack.technologies.map((tech, techIndex) => (
                    <Badge 
                      key={techIndex}
                      variant="outline" 
                      className="bg-secondary/50 border-primary/30 text-foreground hover:bg-primary/20 hover:border-primary/50 transition-all duration-300"
                    >
                      {tech}
                    </Badge>
                  ))}
                </div>
              </Card>
            ))}
          </div>
        </section>

        {/* Philosophy Section */}
        <section className="mb-16">
          <Card className="p-12 bg-gradient-matrix border-accent/20 relative overflow-hidden">
            <div className="absolute inset-0 bg-gradient-to-r from-primary/5 to-accent/5"></div>
            <div className="relative z-10">
              <h2 className="text-3xl font-bold mb-6 text-center text-accent">Computational Philosophy</h2>
              <blockquote className="text-xl text-center text-muted-foreground italic leading-relaxed max-w-4xl mx-auto">
                "In the <span className="text-primary font-semibold">labyrinthine</span> corridors of artificial cognition, 
                I endeavor to transmute the <span className="text-accent font-semibold">ineffable</span> complexity 
                of intelligence into <span className="text-primary font-semibold">tangible</span> algorithms. 
                Each model is a <span className="text-accent font-semibold">tessellation</span> of mathematical 
                precision and creative <span className="text-primary font-semibold">serendipity</span>."
              </blockquote>
            </div>
          </Card>
        </section>

        {/* Contact/Connect Section */}
        <section className="text-center">
          <h2 className="text-3xl font-bold mb-8 bg-gradient-neural bg-clip-text text-transparent">
            Collaborative Ventures
          </h2>
          <p className="text-lg text-muted-foreground mb-8 max-w-2xl mx-auto">
            Seeking fellow <span className="text-accent font-semibold">cognoscenti</span> to explore the 
            <span className="text-primary font-semibold">liminal</span> spaces between artificial and human intelligence.
          </p>
          
          <div className="flex justify-center space-x-6">
            <Badge variant="outline" className="p-3 bg-primary/10 border-primary/30 hover:bg-primary/20 transition-all duration-300 cursor-pointer">
              🔗 GitHub
            </Badge>
            <Badge variant="outline" className="p-3 bg-accent/10 border-accent/30 hover:bg-accent/20 transition-all duration-300 cursor-pointer">
              💼 LinkedIn
            </Badge>
            <Badge variant="outline" className="p-3 bg-primary/10 border-primary/30 hover:bg-primary/20 transition-all duration-300 cursor-pointer">
              📧 Email
            </Badge>
          </div>
        </section>
      </div>
    </div>
  );
};

export default Index;
