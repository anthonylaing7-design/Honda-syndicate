import React, { useState, useEffect } from "react";
    setParts(parts.filter((part) => part.id !== id));
  };

  const filteredParts = parts.filter((part) =>
    part.name.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <motion.h1
        initial={{ opacity: 0, y: -20 }}
        animate={{ opacity: 1, y: 0 }}
        className="text-3xl font-bold mb-6 text-center"
      >
        Honda Civic Parts Sales
      </motion.h1>

      <Card className="mb-6 rounded-2xl shadow-md">
        <CardContent className="p-4 grid gap-4">
          <Input
            placeholder="Part Name"
            value={newPart.name}
            onChange={(e) => setNewPart({ ...newPart, name: e.target.value })}
          />
          <Input
            placeholder="Price"
            type="number"
            value={newPart.price}
            onChange={(e) => setNewPart({ ...newPart, price: e.target.value })}
          />
          <Input
            placeholder="Condition (New/Used)"
            value={newPart.condition}
            onChange={(e) => setNewPart({ ...newPart, condition: e.target.value })}
          />
          <Button onClick={addPart} className="rounded-2xl">
            <Plus className="mr-2 h-4 w-4" /> Add Part
          </Button>
        </CardContent>
      </Card>

      <div className="mb-4 flex items-center gap-2">
        <Search className="h-4 w-4" />
        <Input
          placeholder="Search Parts"
          value={search}
          onChange={(e) => setSearch(e.target.value)}
        />
      </div>

      <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-4">
        {filteredParts.map((part) => (
          <motion.div
            key={part.id}
            initial={{ opacity: 0, scale: 0.9 }}
            animate={{ opacity: 1, scale: 1 }}
          >
            <Card className="rounded-2xl shadow-md">
              <CardContent className="p-4">
                <h2 className="text-xl font-semibold">{part.name}</h2>
                <p className="text-gray-600">Condition: {part.condition}</p>
                <p className="text-lg font-bold mt-2">R {part.price}</p>
                <Button
                  variant="destructive"
                  onClick={() => deletePart(part.id)}
                  className="mt-3 rounded-2xl"
                >
                  <Trash2 className="mr-2 h-4 w-4" /> Delete
                </Button>
              </CardContent>
            </Card>
          </motion.div>
        ))}
      </div>
    </div>
  );
}
